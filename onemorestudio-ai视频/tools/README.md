# tools/

本目录存放**本地工具二进制**，不进入 Git（见根目录 `.gitignore`，仅本文件被放行）。

## ffmpeg

- 版本：ffmpeg 7.1（macOS arm64）
- 路径：`tools/imageio_ffmpeg/binaries/ffmpeg-macos-aarch64-v7.1`
- 来源：`python3 -m pip install --target ./tools imageio-ffmpeg`

### 重装方式（换电脑或目录被清理后）

```bash
cd ~/Desktop/小One剪辑文件/onemorestudio-ai视频
python3 -m pip install --target ./tools imageio-ffmpeg
```

### 常用命令

```bash
FF=./tools/imageio_ffmpeg/binaries/ffmpeg-macos-aarch64-v7.1

# 抽单帧
"$FF" -y -ss 3 -i input.mp4 -frames:v 1 -vf scale=360:-1 out.jpg

# 生成 4x4 抽帧拼图（16 帧）
"$FF" -y -i input.mp4 -vf "fps=0.76,scale=320:-1,tile=4x4" -frames:v 1 sheet.jpg

# 按入出点精确裁剪（无损拼接前先统一编码）
"$FF" -y -ss 00:00:04.5 -to 00:00:12 -i input.mp4 -c copy clip.mp4
```

说明：二进制体积约 80MB，禁止提交到仓库。
