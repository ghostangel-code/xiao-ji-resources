# XiaoJi Docker 镜像
# 多阶段构建，减小最终镜像大小

# 阶段 1: 构建阶段
FROM golang:1.21-alpine AS builder

# 安装构建依赖
RUN apk add --no-cache git ca-certificates tzdata

# 设置工作目录
WORKDIR /build

# 复制 go mod 文件
COPY go.mod go.sum ./
RUN go mod download

# 复制源代码
COPY . .

# 构建二进制文件
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build \
    -ldflags='-w -s -extldflags "-static"' \
    -a -installsuffix cgo \
    -o xiaoji ./cmd/xiaoji

# 阶段 2: 运行阶段
FROM alpine:latest

# 安装运行时依赖
RUN apk --no-cache add ca-certificates ffmpeg python3 py3-pip

# 创建非 root 用户
RUN addgroup -g 1000 -S xiaoji && \
    adduser -u 1000 -S xiaoji -G xiaoji

# 设置时区
ENV TZ=Asia/Shanghai

# 创建工作目录
WORKDIR /app

# 从构建阶段复制二进制文件
COPY --from=builder /build/xiaoji /usr/local/bin/xiaoji

# 设置数据目录
RUN mkdir -p /data && chown -R xiaoji:xiaoji /data
VOLUME ["/data"]

# 切换到非 root 用户
USER xiaoji

# 暴露端口
EXPOSE 8080

# 设置环境变量
ENV XIAOJI_DATA_DIR=/data
ENV XIAOJI_CONFIG_DIR=/data/config

# 健康检查
HEALTHCHECK --interval=30s --timeout=10s --start-period=40s --retries=3 \
    CMD xiaoji health || exit 1

# 启动命令
ENTRYPOINT ["xiaoji"]
CMD ["server"]
