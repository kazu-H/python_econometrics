## はじめに
[Pythonで学ぶ入門計量経済学](https://py4etrics.github.io/index.html)のコンテンツを学習するうえで、Dockerで環境を統一して複数端末で実行したいというモチベがある。この時、vscodeを用いながら適宜gitで管理していきたい。

なお、dockerやvscodeの導入等は以下参考資料のリンク先に譲る。

## 参考資料
- [DockerとVScodeでPython環境構築](https://qiita.com/KiYuRo/items/c016eaf5066c6cedaa11#step4-devcontainerjson%E3%82%92%E4%BD%BF%E7%94%A8%E3%81%99%E3%82%8B)
- [Markdown記法 チートシート](https://qiita.com/Qiita/items/c686397e4a0f4f11683d)
- [Ubuntu on WSL2でのDocker Engineの最短インストール手順](https://qiita.com/nujust/items/d7cd395baa0c5dc94fc5)
- [WSL2(Ubuntu)でGitHubを使用する](https://qiita.com/Michi1090/items/094a13cad3133e97d202)
- [Git クローン(clone)してpushとpullを行う(GitHub)](https://itsakura.com/tool-github-git-ssh) 
- [君には1時間でGitについて知ってもらう(with VSCode)](https://qiita.com/jesus_isao/items/63557eba36819faa4ad9)
- [WSL2のUbuntuでkeychain経由でssh-agentを使う](https://zenn.dev/kaityo256/articles/ssh_agent_on_wsl)

## やること
- Dockerfileの作成
requirement.txtを作成して必要なパッケージを指定しておくこと。
- docker-compose.ymlの作成
- devcontainer.jsonの作成
VSCodeを使うために設定しておく。