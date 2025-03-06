# study-workflow
学习使用github工作流
# 学习来源
## [b站](https://www.bilibili.com/video/BV14F411q7De?spm_id_from=333.788.videopod.episodes&vd_source=9a7a74ff1d725acfc83fd3567cd4a7c4)
# 目录
- [01-first-workflows](01-first-workflows/01.md)
- [02-simple-action](02-simple-action/02.md)
- [03-custom-environment-variables](03-custom-environment-variables/03.md)
- [04-encrypting-environment-variable](04-encrypting-environment-variable/04.md)
- [05-use-github-token](05-use-github-token/05.md)
- [06-encrypt-decrypt](06-encrypt-decrypt/06.md)
- [07-context](07-context/07.md)
- [08-function-expression](08-function-expression/08.md)
- [09-if-check-function](09-if-check-function/09.md)
- [10-use-node](10-use-node/10.md)
- [11-use-strategy](11-use-strategy/11.md)

## 形成上面目录的powershell脚本
```powershell
# 获取当前目录下以数字开头的文件夹
$folders = Get-ChildItem -Directory | Where-Object { $_.Name -match '^\d' }

# 初始化一个字符串数组来存储 Markdown 链接
$markdownLinks = @()

# 遍历文件夹并生成 Markdown 链接
foreach ($folder in $folders) {
    $folderName = $folder.Name
    # 假设每个文件夹下有一个以 "01.md"、"02.md" 等命名的文件
    $linkPath = "$folderName/$($folderName.Split('-')[0]).md"
    $markdownLink = "- [$folderName]($linkPath)"
    $markdownLinks += $markdownLink
}

# 将 Markdown 链接追加到 README.md 文件的末尾
$markdownContent = $markdownLinks -join "`n"
$markdownContent | Add-Content -Path "README.md" -Encoding UTF8

Write-Output "内容已追加到 README.md 文件的末尾。"
```
