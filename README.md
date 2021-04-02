**当リポジトリは以下を実現するためのGitHub Actionsのワークフロー設定([yamlファイル](.github/workflows/main.yaml))の実装例です**

## 実現したいこと
リポジトリに複数あるDockerfileをGitHub Actionsでbuildする  
変更のあったファイルだけをbuildする

```bash:tree
.
├── .github
│   └── workflows
│       └── main.yaml
├── hello
│   ├── Dockerfile
│   └── hello.sh
├── world
│   ├── Dockerfile
│   └── world.sh
└── README.md
```

**ケース1**  
以下のファイルを操作

- /hello/hello.sh(modified)

⇒GitHub Actionsが以下ディレクトリをdocker build

- /hello

**ケース2**  
以下のファイルを操作

- /hello/Dockerfile(new file)
- /hello/hello.sh(new file)
- /world/world.sh(modified)
- /.github/workflows/main.yaml(modified)

⇒GitHub Actionsが以下ディレクトリをdocker build

- /hello
- /world

**ケース3**
以下のファイルを操作

- /README.md(deleted)
- /.github/workflows/main.yaml(modified)

⇒docker buildしない
