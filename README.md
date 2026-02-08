# XiaoJi Resources Mirror

XiaoJi 项目所需的预编译资源镜像仓库。

## 仓库结构

```
xiao-ji-resources/
├── ffmpeg/                 # FFmpeg 预编译二进制文件
│   ├── macos/             # macOS 版本
│   ├── linux/             # Linux 版本
│   └── windows/           # Windows 版本
├── models/                 # 语音模型文件
│   ├── stt/               # 语音识别模型 (SenseVoice)
│   ├── tts/               # 语音合成模型 (VITS)
│   ├── vad/               # 语音活动检测模型 (Silero VAD)
│   ├── kws/               # 唤醒词检测模型
│   └── speaker/           # 声纹识别模型
├── python/                 # 嵌入式 Python 环境
│   ├── macos-arm64/
│   ├── macos-x64/
│   ├── linux-arm64/
│   ├── linux-x64/
│   └── windows-x64/
├── docker/                 # Docker 配置
│   ├── chroma/            # Chroma 向量数据库
│   └── xiaoji/            # XiaoJi 应用镜像
└── docs/                   # 资源来源和许可证信息
    ├── SOURCES.md
    └── LICENSES.md
```

## 资源清单

### 1. FFmpeg

| 平台 | 架构 | 文件名 | 来源 |
|------|------|--------|------|
| macOS | Universal | ffmpeg.zip | evermeet.cx |
| Linux | AMD64 | ffmpeg.tar.xz | johnvansickle.com |
| Linux | ARM64 | ffmpeg-arm64.tar.xz | johnvansickle.com |
| Windows | x64 | ffmpeg.exe | BtbN GitHub Builds |

### 2. 语音模型

#### STT (语音识别)
- **SenseVoice Small INT8**
  - model.onnx (约 239MB)
  - configuration.json
  - tokens.txt
  - 来源: ModelScope

#### TTS (语音合成)
- **VITS Chinese**
  - model.onnx (约 121MB)
  - lexicon.txt
  - tokens.txt
  - 来源: HuggingFace

#### VAD (语音活动检测)
- **Silero VAD**
  - silero_vad.onnx (约 1MB)
  - 来源: k2-fsa/sherpa-onnx

#### KWS (唤醒词检测)
- **Zipformer Wenetspeech**
  - model.tar.bz2 (约 3.3MB)
  - 来源: k2-fsa/sherpa-onnx

#### Speaker (声纹识别)
- **ERes2Net**
  - model.onnx (约 50MB)
  - 来源: k2-fsa/sherpa-onnx

### 3. 嵌入式 Python

| 平台 | 架构 | 版本 | 来源 |
|------|------|------|------|
| macOS | ARM64 | 3.10.13 | indygreg/python-build-standalone |
| macOS | x64 | 3.10.13 | indygreg/python-build-standalone |
| Linux | ARM64 | 3.10.13 | indygreg/python-build-standalone |
| Linux | x64 | 3.10.13 | indygreg/python-build-standalone |
| Windows | x64 | 3.10.13 | indygreg/python-build-standalone |

### 4. Docker 镜像

#### Chroma 向量数据库
- **镜像**: `chromadb/chroma:latest`
- **用途**: 长期记忆存储
- **端口**: 8000
- **验证**: ✅ 已验证可下载

#### XiaoJi 应用 (可选)
- **镜像**: `ghcr.io/ghostangel-code/xiaoji:latest`
- **用途**: 完整应用容器化部署
- **端口**: 8080
- **包含**: FFmpeg、Python、语音模型

## Docker 使用

### 启动 Chroma

```bash
cd docker/chroma
docker-compose up -d
```

### 构建 XiaoJi 镜像

```bash
cd docker/xiaoji
docker build -t xiaoji:latest .
```

### 运行 XiaoJi

```bash
docker run -d \
  --name xiaoji \
  -p 8080:8080 \
  -v $(pwd)/data:/data \
  -e XIAOJI_DATA_DIR=/data \
  xiaoji:latest
```

## 原始来源

- **FFmpeg**: https://ffmpeg.org/
  - macOS: https://evermeet.cx/ffmpeg/
  - Linux: https://johnvansickle.com/ffmpeg/
  - Windows: https://github.com/BtbN/FFmpeg-Builds

- **Python**: https://github.com/indygreg/python-build-standalone

- **语音模型**: https://github.com/k2-fsa/sherpa-onnx

- **SenseVoice**: https://modelscope.cn/models/poloniumrock/SenseVoiceSmallOnnx

- **VITS**: https://huggingface.co/csukuangfj/sherpa-onnx-vits-zh-ll

- **Chroma**: https://github.com/chroma-core/chroma

## 许可证

各资源遵循其原始项目的许可证：
- FFmpeg: GPL/LGPL
- Python: PSF License
- Sherpa-ONNX: Apache 2.0
- SenseVoice: 原始项目许可证
- Chroma: Apache 2.0

详见 [docs/LICENSES.md](docs/LICENSES.md)

## 使用说明

在 XiaoJi 安装过程中，程序会自动从此仓库下载所需资源。

如需手动下载，请访问 GitHub Releases 页面获取最新版本。

## 更新记录

- 2026-02-08: 初始创建，整理所有资源清单
- 2026-02-08: 添加 Docker 配置（Chroma、XiaoJi Dockerfile）
