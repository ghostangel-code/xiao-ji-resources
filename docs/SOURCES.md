# 资源来源清单

本文档列出所有资源的原始下载链接和来源。

## Docker 软件

### macOS
- **Docker Desktop**: https://www.docker.com/products/docker-desktop/
- **下载链接**: https://desktop.docker.com/mac/main/arm64/Docker.dmg (Apple Silicon)
- **下载链接**: https://desktop.docker.com/mac/main/amd64/Docker.dmg (Intel)
- **Homebrew**: `brew install --cask docker`

### Linux
- **官方安装脚本**:
  ```bash
  curl -fsSL https://get.docker.com -o get-docker.sh
  sh get-docker.sh
  ```
- **手动安装**:
  - Ubuntu/Debian: https://docs.docker.com/engine/install/ubuntu/
  - CentOS/RHEL: https://docs.docker.com/engine/install/centos/
  - Fedora: https://docs.docker.com/engine/install/fedora/

### Windows
- **Docker Desktop**: https://www.docker.com/products/docker-desktop/
- **下载链接**: https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe
- **说明**: Windows 10/11 64位专业版或企业版

## FFmpeg

### macOS
- **来源**: https://evermeet.cx/ffmpeg/
- **下载链接**: https://evermeet.cx/ffmpeg/getrelease/ffmpeg/zip
- **说明**: 静态构建版本，支持 Intel 和 Apple Silicon

### Linux
- **来源**: https://johnvansickle.com/ffmpeg/
- **AMD64**: https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-amd64-static.tar.xz
- **ARM64**: https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-arm64-static.tar.xz
- **说明**: 静态构建，无需依赖

### Windows
- **来源**: https://github.com/BtbN/FFmpeg-Builds
- **下载链接**: https://github.com/BtbN/FFmpeg-Builds/releases/download/latest/ffmpeg-master-latest-win64-gpl.zip
- **说明**: GPL 版本，包含完整功能

## Python 嵌入式环境

- **来源**: https://github.com/indygreg/python-build-standalone
- **版本**: 3.10.13
- **发布页**: https://github.com/indygreg/python-build-standalone/releases/tag/20240107

### 下载链接模板
```
https://github.com/indygreg/python-build-standalone/releases/download/20240107/cpython-{version}+20240107-{platform}-install_only.tar.gz
```

### 平台特定链接
- macOS ARM64: `cpython-3.10.13+20240107-aarch64-apple-darwin-install_only.tar.gz`
- macOS x64: `cpython-3.10.13+20240107-x86_64-apple-darwin-install_only.tar.gz`
- Linux ARM64: `cpython-3.10.13+20240107-aarch64-unknown-linux-gnu-install_only.tar.gz`
- Linux x64: `cpython-3.10.13+20240107-x86_64-unknown-linux-gnu-install_only.tar.gz`
- Windows x64: `cpython-3.10.13+20240107-x86_64-pc-windows-msvc-install_only.tar.gz`

## 语音模型

### 1. SenseVoice 语音识别模型

**来源**: ModelScope
- **模型页面**: https://modelscope.cn/models/poloniumrock/SenseVoiceSmallOnnx

**文件清单**:
- model.int8.onnx: https://modelscope.cn/models/poloniumrock/SenseVoiceSmallOnnx/resolve/master/model.int8.onnx
- configuration.json: https://modelscope.cn/models/poloniumrock/SenseVoiceSmallOnnx/resolve/master/configuration.json
- tokens.txt: https://modelscope.cn/models/poloniumrock/SenseVoiceSmallOnnx/resolve/master/tokens.txt

**说明**: INT8 量化版本，约 239MB，支持多语言识别

### 2. VITS 中文语音合成模型

**来源**: HuggingFace
- **模型页面**: https://huggingface.co/csukuangfj/sherpa-onnx-vits-zh-ll

**文件清单**:
- model.onnx: https://huggingface.co/csukuangfj/sherpa-onnx-vits-zh-ll/resolve/main/model.onnx
- lexicon.txt: https://huggingface.co/csukuangfj/sherpa-onnx-vits-zh-ll/resolve/main/lexicon.txt
- tokens.txt: https://huggingface.co/csukuangfj/sherpa-onnx-vits-zh-ll/resolve/main/tokens.txt

**说明**: 约 121MB，支持中文语音合成

### 3. VAD 语音活动检测模型

**来源**: k2-fsa/sherpa-onnx
- **下载链接**: https://github.com/k2-fsa/sherpa-onnx/releases/download/asr-models/silero_vad.onnx
- **说明**: Silero VAD 模型，约 1MB

### 4. 唤醒词检测模型

**来源**: k2-fsa/sherpa-onnx
- **下载链接**: https://github.com/k2-fsa/sherpa-onnx/releases/download/kws-models/sherpa-onnx-kws-zipformer-wenetspeech-3.3M-2024-01-01.tar.bz2
- **说明**: Zipformer 架构，约 3.3MB

### 5. 声纹识别模型

**来源**: k2-fsa/sherpa-onnx
- **下载链接**: https://github.com/k2-fsa/sherpa-onnx/releases/download/speaker-recongition-models/3dspeaker_speech_eres2net_base_sv_zh-cn_3dspeaker_16k.onnx
- **说明**: ERes2Net 架构，3D-Speaker 数据集训练，约 50MB

## 其他资源

### Homebrew 安装脚本
- **来源**: https://brew.sh/
- **脚本链接**: https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh

### FRP 内网穿透工具
- **来源**: https://github.com/fatedier/frp
- **发布页**: https://github.com/fatedier/frp/releases

## 相关项目

- **XiaoJi Core**: https://github.com/ghostangel-code/xiao-ji
- **Sherpa-ONNX**: https://github.com/k2-fsa/sherpa-onnx
- **SenseVoice**: https://github.com/FunAudioLLM/SenseVoice
- **FFmpeg**: https://ffmpeg.org/
- **Docker**: https://www.docker.com/
