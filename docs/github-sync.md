# Windows 和 Android 同步教程

准备两台装有 Day by Day 1.0 的设备和一个自己的 GitHub 账号。只想在单台设备使用时，可以跳过整个教程。若两台设备已有记录，先分别到「数据与来源」导出完整 JSON 备份。

## 1. 创建存记录的私有仓库

1. 登录 GitHub，打开 [新建仓库](https://github.com/new)。`Owner` 选择你自己的账号，`Repository name` 填 `habit-journal-sync`。仓库名可以自定，后面要照填。
2. 可见性选 **Private**，打开 **Add README**，再点 **Create repository**。添加 README 会创建第一个提交，让应用能找到分支。
3. 在新仓库的文件列表上方找到分支名，通常是 `main`。记下自己的用户名、仓库名、分支名。应用会自动创建同步文件。

Day by Day 的公开下载仓库用于发安装包。你的打卡和笔记会写入刚建的私有仓库，GitHub 会保留历史版本。记录以可读的 JSON 保存，请仅让你信任的人访问仓库。

## 2. 创建访问令牌

1. 打开 [创建细粒度令牌](https://github.com/settings/personal-access-tokens/new)。`Token name` 填 `Day by Day Sync`，设置一个你方便续期的有效期，`Resource owner` 选择你自己。
2. 在 `Repository access` 选 **Only select repositories**，只勾选刚创建的 `habit-journal-sync`。
3. 在 `Permissions` 的仓库权限里添加 **Contents**，设为 **Read and write**。其他权限保持默认，`Metadata` 如果自动显示为只读，保留即可。检查后点击 **Generate token**。
4. 令牌相当于这一个仓库的访问密码。生成后直接复制到应用的「访问令牌」输入框。请勿发到聊天、邮件、截图或 GitHub Issue。你也可以为安卓单独创建一个权限相同的令牌，方便以后分别更换。 [GitHub 官方令牌说明](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)

## 3. 先在 Windows 配置，再配置 Android

1. Windows 打开「数据与来源 → GitHub 同步 → 连接私有仓库」，按下表填写，点 **保存并连接**。已有旧 HTML 记录时，可以先用「数据与来源」导入完整 JSON 备份。

   | 应用里的字段 | 填什么 |
   | --- | --- |
   | 仓库所有者 | GitHub 用户名，例如 `example-user` |
   | 仓库名称 | `habit-journal-sync`，只填名称 |
   | 分支 | 仓库文件列表上方显示的分支，通常是 `main` |
   | 访问令牌 | 上一步生成的令牌 |

2. 在 Windows 的 Today 下方写一条测试笔记，例如「Windows 同步测试」，回到「数据与来源」等状态变成 **已同步**。也可以按 **立即同步**。
3. Android 进入同一个设置页面，填写同样的仓库所有者、名称、分支，以及有该仓库读写权限的令牌。点「保存并连接」，看到「已同步」后回 Today 核对同一天的笔记。
4. 在 Android 把笔记改成「Android 同步测试」，等手机显示「已同步」。切回 Windows，按「立即同步」，确认看到修改。两台设备都能收到对方的修改，首次配置就完成了。

## 日常使用和排查

| 看到什么 | 怎么办 |
| --- | --- |
| 刚改完，另一端还没出现 | 先让修改的一端显示「已同步」。接收的一端打开应用、切回前台，或在数据页点「立即同步」。应用在前台约每 30 秒检查一次，网络慢时需要更久。关闭应用后同步会暂停。 |
| 待上传或连接失败 | 本机已保存的内容可以继续编辑。检查网络，恢复后应用会重试。 |
| 找不到仓库或分支 | 核对仓库所有者、名称和分支，确认仓库是 Private、已经添加 README，并在令牌范围内。 |
| 需要重新授权 | 核对令牌的有效期和 Contents 读写权限，必要时生成新令牌。在「仓库与授权设置」保存。 |
| 需要处理冲突 | 两台设备都改了同一项时，进入「数据与来源」，查看本机和 GitHub 的内容，选要保留的一方后点「应用选择并同步」。如果界面提示重新复盘，回对应日期确认。 |

换设备或卸载应用前，可以到「数据与来源」导出完整 JSON。CSV 适合表格查看，恢复记录请选 JSON 备份。

[返回下载和功能介绍](../README.md) · [复制 Codex 懒人提示词](codex-sync-prompt.md)
