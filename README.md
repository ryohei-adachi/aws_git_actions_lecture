# ① Gitリポジトリの構築とテストプッシュ

+ GitHubにログインする

<br>

https://github.com/

<br><br>

+ ホーム画面のTop RepositoryのNewボタンを選択する。

<br>

<img src="https://github.com/user-attachments/assets/f64eb535-9232-44bd-9bd0-32e5b17ea589" width="70%" />

<br><br>

+ 「Create a new repository」画面で、Repository nameを入力して、「Create repository」ボタンを押下。
    + 本手順では、「git_aws_cicd_lecture」とリポジトリ名を記入
    + 「Add a README file」のチェックボックスは外しておく

<br>

<img src="https://github.com/user-attachments/assets/43d7cb36-da8c-413b-bdff-94ccba105f14" width="70%" />
<br>
<img src="https://github.com/user-attachments/assets/93f59745-5487-464a-ae0f-a81199ecbc55" width="70%" />

<br>

下記画面が表示されれば、OK。

<br>

<img src="https://github.com/user-attachments/assets/96240a57-1dcd-49e6-9ba9-f6eed248f5b1" width="70%" />

<br><br>

+ パーソナルアクセストークンを発行する

<br>

右上のアカウントメニューから「Settings」を選択

<br>

<img src="https://github.com/user-attachments/assets/3154412a-6c44-4f0e-b44a-7f04115366ca" width="70%" />

<br>

左メニューから「Developer settings」

<img src="https://github.com/user-attachments/assets/ff6625e9-67ae-4b63-a8fa-09fd3df12d14" width="70%" />

<br>

「Generate new token」をクリックして、「Fine-grained tokens」を選択

<br>

<img src="https://github.com/user-attachments/assets/ba0c8304-8c63-4fde-9d1c-6175d667c73c" width="70%" />

<br>

アクセストークンの名前、有効期限を入力して、「Generate token」をクリック。

<br>

<img src="https://github.com/user-attachments/assets/32ec5116-761e-4343-8355-22caeb2bb709" width="70%" />

<br>

生成されたアクセストークンをコピー＆保管する

<br>

<img src="https://github.com/user-attachments/assets/cbd586d5-5ca0-416f-8adb-5b7a76ceb922" width="70%" />


<br>
<br>

+ Gitにユーザ名とメールアドレスを登録

<br>

ターミナル(Windowsの方はコマンドプロンプト)を開き、下記コマンドを入力する。

<br>

```
git config --global user.name "(ユーザ名)"
git config --global user.email "(メールアドレス)"
```

<br><br>

+ ローカルリポジトリを作成する

<br>


ターミナルに下記コマンドを入力する。
(PCの任意のフォルダに移動して、git initコマンドを入力する)

<br>

```
cd (任意のフォルダのパス)
git init
```

<br>
<br>

+ ローカルリポジトリにテストファイルを作成する

<br>

.gitフォルダが存在する場所に、任意のファイルを作成する。

<br>

<img src="https://github.com/user-attachments/assets/c74e9858-9784-4849-9e69-3f8e2dbbc044" width="70%" />


<br>
<br>

+ GitHubにプッシュする

<br>

ターミナルに下記コマンドを入力する

<br>

```
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/(ユーザ名)/(リポジトリ名).git
git push -u origin main
```

<br>
<br>

+ GitHubにアクセスして、テストファイルがアップロードされていることを確認する

# ② AWS EC2の構築

<br>

+ AWSにログインする。

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/4c8cec3b-b46a-4e04-a90c-f5378e9f63a6" width="70%" />

<br><br>

+ AWSのマジメントコンソールを開き、リージョンを選択する
  + 本手順書では、「東京」リージョンに選択したうえで進める。

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/a5490b76-9d0d-4306-a100-3adc8b9fc3b4" width="70%" />

<br><br>

+ マネジメントコンソールの検索部分に「EC2」と入力・検索を行い、EC2サービスを選択する。

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/2704af17-6537-492f-bd55-61f00c010825" width="70%" />

<br><br>

+ 左メニューの「インスタンス」を選択して、「インスタンスを起動」をクリックする。

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/17c66e10-3095-41e4-9baf-dd799a6c5549" width="70%" />

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/6025e6ac-d8d2-4207-a74b-96a10b8a4af5" width="70%" />

<br><br><br>

+ 「Launch an instance」では下記の内容を入力・選択する
  + 名前: 好きなサーバ名を入力してください
  + Amazon マシンイメージ (AMI): Amazon Linux 2023
  + インスタンスタイプ: t2.micro
  + ネットワークの設定: パブリックIPの自動割り当てを「無効」から「有効」に変えてください
  + キーペア (ログイン) : 新しいキーペアの作成をクリックして、キーペアを取得してください(ログイン時に使用)
    +  キーペア名: 好きな名前を入力してください
    +  キーペアのタイプ: RSA
    +  プライベートキーファイル形式: 「.pem」
      
<br><br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/05e292b4-55e6-48bd-addd-05e5a4ee682a" width="70%" />

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/26f81d98-07d2-482e-b37f-545b5e72b1cb" width="70%" />

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/ecc10718-aa70-4d39-b9fa-bd925ce0855b" width="70%" />

<br><br>


<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/71602f1e-f76d-49af-9ba6-c0a4c516c517" width="70%" />

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/fa4d93e0-3cdd-4857-861f-9e032e38ca76" width="70%" />

<br><br>

必要項目を入力をした後、「キーペアを作成」をクリックする。

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/63254121-0875-47eb-a8c0-6c0e7958e3bd" width="70%" />

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/0a398555-165a-44e3-a2e3-99fe68664a05" width="70%" />

<br><br>

ネットワークの設定ボタンをクリックし、パブリックIPの自動割り当てを「有効」にする。

+ 上記の内容の入力が出来ましたら、「インスタンスを起動」をクリックする。

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/027944c3-56a1-4af5-b2fb-926cc96ef7a5" width="70%" />

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/84c14c41-10c4-4426-8f9f-7f7cee0712c2" width="70%" />

<br><br>

+ 「すべてインスタンスを表示」を選択して、EC2インスタンスが作成されていることを確認する。

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/96175ed0-8179-4b81-b0be-32a5dbdd3809" width="70%" />

<br><br>

+ セキュリティグループを設定する

作成したインスタンスを選択した状態で、「セキュリティタブ」を開き、セキュリティグループを選択する。
⇒ 「sg-XXXXXXXXX」というセキュリティグループIDがEC2インスタンスに付与されている

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/c163515d-366b-4ae7-a47d-61923e0f4bad" width="70%" />

<br>

セキュリティグループの設定画面を開き、「インバウンドのルールを編集」をクリックする

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/cfcaf86d-227c-4f50-90c6-7172533f248a" width="70%" />

<br><br>

以下のルールを追加して、「ルールを保存」ボタンをクリックしてください。
  + タイプ: SSH
    + ソース: Anywhere-IPv4
  + タイプ: HTTP
    + ソース: Anywhere-IPv4

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/bc998a8c-580f-4b45-97e2-cb4e502a502d" width="70%" />

<br><br>

+ EC2インスタンスにssh接続する

EC2インスタンスのパブリックIPアドレスを確認する。

<br><br>

 <img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/6a27c26e-1eb6-49d9-b2f4-053dac0427c5" width="70%" />

 ### Windowsユーザの方

<br>

Tera Term5を開き、ホストにEC2インスタンスのパブリックIPアドレスを入力して、OKをクリックする。

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/1f36595f-3aec-4143-8288-d1e1b2609e94" width="50%" />

<br><br>

続行をクリックする。

<br><br>

 <img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/3070e9e4-f7dd-497b-807a-747d28b307b9" width="50%" />

<br><br>

ユーザ名に「ec2-user」、認証方式は「RSA/DSA/ECDSA/ED25519鍵を使う」を選択する。

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/7a691b46-2d8f-47bc-8bbb-70d53c1e29a9" width="50%" />

<br><br>

秘密鍵の個所に、EC2インスタンス作成時に生成したキーペア(.pemファイル)を指定する。

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/4e289e7a-a83b-4b6f-a47d-58174764999e" width="50%" />

<br><br>

 <img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/e7aca950-e189-40d5-b891-4b692663c529" width="50%" />

<br><br>

 <img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/67ca8b9b-dd7f-4dff-b31a-87c053732fea" width="50%" />

「OK」をクリックして、EC2インスタンスに入れることを確認する。

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/f8dfc541-f812-4cff-8cfa-a1c0a4065b10" width="50%" />

<br><br>

### Macユーザの方

Launchpadから「ターミナル」を開く。

<img width="70%" alt="image" src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/8c8ee8a8-c08b-4d9f-98db-7d7a6a447831">

<br><br>

<img width="70%" alt="image" src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/dd2dcb30-f638-49f0-abc4-9534aa0caf29">

<br><br>

ターミナル上に以下のコマンドを入力する。
　⇒ ダウンロードしたキーペアを「~/.ssh」配下に移動させて、権限変更を行う。

<br><br>

```
mv /Users/(Macのユーザ名)/Downloads/（キーペア名）.pem  ~/.ssh
chmod 600 /Users/(Macのユーザ名)/.ssh/(キーペア名).pem
```

<br><br>

<img width="70%" alt="image" src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/eb021bfb-197b-47dd-882e-ca31e0c33432">

<br><br>

ターミナル上に以下のコマンドを入力する。
　⇒ sshコマンドを使って、EC2インスタンスにログインする。

<br><br>

```
ssh -i /Users/(Macのユーザ名)/.ssh/(キーペア名).pem ec2-user@(EC2のパブリックIPアドレス)
```

<br><br>

「Are you sure you want to continue connecting (yes/no/[fingerprint])?」というメッセージが出た場合、「Yes」と入力する。


<img width="70%" alt="image" src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/b5c6be6a-d994-4e3c-8619-332ba186ea51">

<br><br>

EC2インスタンスからログアウトしたい時は以下のコマンドを実行する。

```
exit
```

<br><br>

+ Apacheをインストールする。

<br>

ターミナルに下記のコマンドを入力する。

<br>

```
sudo dnf update
sudo dnf install -y httpd
sudo chmod 777 -R /var/www/html/
```

<br><br>

# ③ GitHub Actionsによる自動デプロイ機能作成

<br>

+ Secretsの登録

GitHubのページから[Settings] > [Secrets and variables] > [Actions]の順に選択する。

<br>

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/7d663b7a-0461-4888-831b-a7211419dfeb">

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/c5008726-9497-4170-bf95-fb7b4aa1e555">

<br>

そして、[Secrets]タブを開き、[New repository secret]をクリックする。

<br>

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/077edecc-b6bf-4bb7-8b66-340d4cc2a761">

<br>

下記の[Name]と[Secret]を入力して、[Add secret]をクリックする。

<br>

| Name | Secret |
| ---- | ---- |
| EC2_HOST | AWS EC2のIPアドレス |
| EC2_SSH_KEY | AWS EC2の秘密鍵(pemファイル)の中身 |
| EC2_USER | "ec2-user"と入力 |

<br>

AWS EC2の秘密鍵の入力については、余計な改行を含めないこと。

<br>

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/9f1c05d8-74e6-4da0-bc58-982d36e9a95f">

<br>

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/3230f2bd-bfcf-42d7-9c0a-b065a71652ff">

<br>

+ ワークフローファイルの作成

①で作成したローカルリポジトリに、「.github/workflows」フォルダを作成する。
「.github/workflows」フォルダに「deploy.yml」というワークフローファイルを作成する。

<br>

```
└ .github/
    └ workflows/
        └ deploy.yml   #ワークフローファイル

```

<br><br>

+ ワークファイルの中身の記載

<br>

「./github/workflows/deploy.yml」に下記の内容を記載して、保存する。

<br>

```
name: Deploy to AWS EC2
on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: リポジトリチェックアウト
        uses: actions/checkout@v4

      - name: SSH設定
        run: |
          echo "${{ secrets.EC2_SSH_KEY }}" > private_key.pem
          chmod 600 private_key.pem
          mkdir ~/.ssh
          ssh-keyscan -H ${{ secrets.EC2_HOST }} >> ~/.ssh/known_hosts
        
      - name: EC2にHTML/CSSをデプロイ
        run:
          rsync -rlOtcv --delete -e "ssh -oStrictHostKeyChecking=no -i private_key.pem" ./web/ ${{ secrets.EC2_USER }}@${{ secrets.EC2_HOST }}:/var/www/html/
        
      - name: EC2でApacheを再起動（オプション）
        run: |
          ssh -i private_key.pem ${{ secrets.EC2_USER }}@${{ secrets.EC2_HOST }} "sudo systemctl restart httpd"
```

<br><br>

+ 本GitHubリポジトリからダウンロードした「web」フォルダーをダウンロードする


<br>
GitHubリポジトリ(aws_git_actions_lecture)の「<>Code」から「Download ZIP」をクリックする。

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/b461f977-5928-46d9-8003-e62199d6e15f">

