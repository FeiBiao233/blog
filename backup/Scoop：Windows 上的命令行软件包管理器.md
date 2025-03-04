
# Scoop：Windows 上的命令行软件包管理器

厌倦了在 Windows 上安装软件时无休止的“下一步”点击？ 想要一个更轻量级、更便捷的软件包管理方式？ 那么 Scoop 就是你的答案！

## Scoop 是什么？

Scoop 是一款专为 Windows 设计的**命令行**软件包管理器。 它可以让你像在 Linux 上使用 `apt` 或 `yum` 一样，通过简单的命令安装、更新和卸载软件。 Scoop 的主要优点包括：

*   **轻量级**: Scoop 非常小巧，不会占用过多系统资源。
*   **命令行操作**:  告别繁琐的图形界面，所有操作都在命令行中完成，更加高效。
*   **无需“下一步”点击**:  一键安装，自动完成所有配置，省时省力。
*   **避免权限问题**: 默认安装在用户目录下，无需管理员权限。
*   **易于清理**: 卸载软件时，会自动删除所有相关文件和配置，保持系统清洁。

## 安装 Scoop

安装 Scoop 非常简单，只需按照以下步骤操作：

1.  **打开 PowerShell**: 以管理员身份运行 PowerShell。
2.  **设置执行策略**:  如果之前没有设置过，需要运行以下命令来允许执行本地脚本：

    ```powershell
    Set-ExecutionPolicy RemoteSigned -scope CurrentUser
    ```

3.  **安装 Scoop**: 复制并粘贴以下命令到 PowerShell 中并运行：

    ```powershell
    irm get.scoop.sh | iex
    ```

    或者使用国内镜像：

    ```powershell
    iwr -useb get.scoop.sh | iex
    ```
详细安装步骤可以参考：[https://gitee.com/scoop-installer/scoop](https://gitee.com/scoop-installer/scoop)

### 注意事项

*   **Git 安装问题**:  Scoop 依赖 Git 来下载软件包信息。 如果你没有科学上网环境，安装 Git 可能会很慢甚至失败。  建议先配置好科学上网环境，或者尝试使用国内的 Git 镜像。

## Scoop 的 Bucket 概念

Scoop 的一个核心概念是 "bucket"。  你可以把它想象成一个软件仓库，里面包含了大量软件的安装信息。  每个 bucket 都是一个 Git 仓库，里面存储的是软件的 "manifest" 文件（通常是 JSON 格式）。

*   **Manifest 文件**:  Manifest 文件描述了如何下载、安装和配置一个软件。  它包含了软件的下载地址、依赖关系、安装脚本等信息。
*   **添加 Bucket**:  Scoop 默认只包含 `main` bucket。  你可以通过 `scoop bucket add <bucket-name> <bucket-url>` 命令添加更多的 bucket，例如 `extras`, `versions` 等，来获取更多软件。

## 我的 Scoop 安装软件列表

以下是我使用 Scoop 安装的一些常用软件：

```
Installed apps:

Name                 Version            Source                       Updated             Info
----                 -------            ------                       -------             ----
7zip                 24.09              main                         2025-02-13 14:34:28
adb                  35.0.2             main                         2025-02-13 18:50:16
anaconda3            2024.10-1          extras                       2025-02-24 10:20:23
aria2                1.37.0-1           main                         2025-02-13 13:48:57
BaiduNetdisk_abgox   7.52.0             kkzzhizhou_scoop-apps        2025-02-13 20:22:32
chatbox              1.9.8              kkzzhizhou_scoop-apps        2025-02-14 10:27:35
cherry-studio        1.0.4              ShuguangSun_sgs-scoop-bucket 2025-03-03 11:03:11
dark                 3.14               main                         2025-02-13 14:58:34
epic-games-launcher  17.2.0             games                        2025-02-14 08:10:45
everything           1.4.1.1026         extras                       2025-02-13 13:51:05
ffmpeg               7.1                main                         2025-02-13 18:52:58
geekuninstaller      1.5.2.165          extras                       2025-02-13 13:52:44
git                  2.48.1             main                         2025-02-27 21:52:53
googlechrome         133.0.6943.60      extras                       2025-02-13 14:06:53
innounp              2.64.1             main                         2025-02-13 20:20:12
LeiGod-Acc           11.0.0.3           xrgzs_sdoog                  2025-02-25 20:52:34
mingw                14.2.0-rt_v12-rev1 main                         2025-02-14 10:09:57
motrix               1.8.19             extras                       2025-02-13 14:18:25
obs-studio           31.0.1             extras                       2025-02-18 23:43:33
ollama               0.5.7              main                         2025-02-13 14:45:32
potplayer            241211             extras                       2025-02-13 14:47:59
powertoys            0.88.0             extras                       2025-02-13 15:00:21
python313            3.13.2             versions                     2025-02-24 13:56:01
python38             3.8.10             versions                     2025-02-24 13:55:47
scrcpy               3.1                main                         2025-02-13 13:49:53
simplenote           2.23.0             extras                       2025-02-13 21:18:32
steam                nightly-20250213   versions                     2025-02-13 14:16:15
tencent-meeting      3.30.11.434        jat001_scoop-ox              2025-02-14 10:50:37
tesseract4           4.1.0-elag2019     versions                     2025-03-01 15:39:13
tesseract4-languages 4.1.0              versions                     2025-03-01 15:42:54
vscode               1.97.2             extras                       2025-02-25 12:09:40
yesplaymusic         0.4.8-2            extras                       2025-02-13 19:21:04
```

## 小技巧：如何使用 Scoop 切换全局 Python 版本

Scoop 允许你安装多个 Python 版本，并轻松切换全局 Python 环境。

1.  **不要安装 `main` bucket 里的 Python**:  `main` bucket 中的 Python 版本可能不是你想要的特定版本。
2.  **使用 `versions` bucket 安装 Python**:  `versions` bucket 提供了各种 Python 版本的 manifest 文件。 例如，`python313` 对应 Python 3.13.2，`python38` 对应 Python 3.8.10。

    ```powershell
    scoop install python313
    scoop install python38
    ```

3.  **切换全局 Python 版本**:  默认情况下，后安装的 Python 版本会被设置为全局 Python 环境。  如果你想切换到其他版本，可以使用 `scoop reset` 命令。

    ```powershell
    scoop reset python313  # 将全局 Python 切换到 3.13.2
    ```

    `scoop reset` 命令实际上是重新安装指定版本的 Python，并将其设置为全局环境。

## 总结

Scoop 是一款非常优秀的 Windows 软件包管理器，它可以让你更方便、更快捷地安装和管理软件。  如果你是 Windows 用户，并且喜欢使用命令行，那么 Scoop 绝对值得一试！
