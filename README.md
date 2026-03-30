# Docker 镜像导出

这个仓库用于通过 GitHub Actions 导出 Docker 镜像为 tar 文件。

## 使用方法

### 1. 推送这个仓库到你的 GitHub

```bash
cd docker-export
git init
git add .
git commit -m "Add Docker image export workflow"
# 创建新仓库后推送
git remote add origin https://github.com/YOUR_USERNAME/docker-export.git
git push -u origin main
```

### 2. 运行 Workflow

1. 打开你的 GitHub 仓库页面
2. 点击 **Actions** 标签
3. 选择左侧的 **Export Docker Image** workflow
4. 点击 **Run workflow**
5. 确认镜像名称是 `docker.1ms.run/vllm/vllm-openai:v0.18.0`
6. 点击 **Run workflow** 按钮

### 3. 下载导出的镜像

1. Workflow 运行完成后（约 5-10 分钟）
2. 在 Actions 页面点击刚完成的运行记录
3. 滚动到页面底部，找到 **Artifacts** 部分
4. 点击 `docker-image-xxx` 下载 tar 文件

### 4. 本地导入镜像

下载完成后，在本地使用：

```bash
docker load -i docker_1ms_run_vllm_vllm-openai_v0_18_0.tar
```

然后就可以正常使用这个镜像了：

```bash
docker run --rm docker.1ms.run/vllm/vllm-openai:v0.18.0 --help
```

## 注意事项

- Artifact 保留 7 天，请及时下载
- 镜像文件可能较大（几 GB），下载需要一定时间
- 如果 GitHub Actions 拉取慢，可以考虑更换镜像源

## 自定义镜像

如果需要导出其他镜像，在运行 workflow 时修改 `image_name` 参数即可。
