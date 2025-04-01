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

※アクセストークンは後に使用する。

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

GitPushするタイミングで下記のようにパスワードを聞かれた場合、
Usernameにはリポジトリに割り当てられたユーザ名、Passwordには先ほどメモしたアクセストークンを入力する。

```
Username for 'https://github.com': 
Password for 'https://xxx@github.com':
```

<br>

+ キーチェーンアクセスへのトークン登録(Macユーザ対象)

<br>

GitPushするたびに、アクセストークンを入力するのが煩わしいため、
自動でアクセストークン認証を実施する方法を紹介。

<br>

Launchpad(あるいは、Spotlight) > キーチェーンアクセス > 検索ボックスに「github.com」と検索する。

<br>
<img src="https://github.com/user-attachments/assets/e530a66b-eb09-430f-b6b0-2048940f9aa4" width="70%" />

<br>
github.comの項目に対して、「パスワードを表示」をクリックして、先ほど発行されたアクセストークンを入力する。

<br>


<img src="https://github.com/user-attachments/assets/14132712-525d-49c9-a57e-22cb9282e63a" width="70%" />

<br>

<img src="https://github.com/user-attachments/assets/9a862c63-4eef-4463-b1b9-9900e63be169" width="70%" />

<br>

以上で、Git操作を行うと、自動でアクセストークン認証をしてくれる。
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

+ マネジメントコンソールの検索部分に「S3」と入力・検索を行い、S3サービスを選択する。

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/f12186eb-be0b-4460-8c98-ac2ab80b7d2a" width="70%" />

<br><br>

<br><br>

+ S3トップ画面の「バケットの作成」をクリックする

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/0fc09c94-edbb-494f-9b1f-865ec0784724" width="70%" />

<br><br>

+ 下記の項目の入力を行う
  + バケット名: (好きな名前) ※但し、世界中の全AWSユーザ間で唯一(一意)の名前にしないといけない
  + パブリックアクセスをすべてブロックのチェックを外す
  + 現在の設定により、このバケットとバケット内のオブジェクトが公開される可能性があることを承認します。にチェックを入れる

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/68f0cf77-5fdc-4f0c-b30f-13afe7707195" width="70%" />

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/f46a6745-6d91-4101-8711-b77bfd3e4586" width="70%" />

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/abed2e67-9b69-4fd3-af1e-c50863840f2a" width="70%" />

<br><br>
上記以外の項目は、変更なしで、「バケットの作成」をクリックする

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/0f5bcebb-a4cc-428c-8883-d505a1a232f2" width="70%" />

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/f62b5885-ae68-41c0-b00e-c4188d4c91ce" width="70%" />

<br><br>

+ 作成したバケットを選択して、「プロパティ」を選択する

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/e300f69a-53cb-445c-ae84-78195ed80a3d" width="70%" />

<br><br>

+ 一番下にある「静的ウェブサイトホスティング」の編集ボタンをクリックする

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/3b211eb9-8fb9-48dd-a91b-3bb2df5b2136" width="70%" />

<br><br>

+ 「静的ウェブサイトホスティングを編集」において、静的ウェブサイトホスティングを「有効」にする

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/31e09796-5917-4b20-bcfe-4ec587c09fbf" width="70%" />

<br><br>

+ インデックスドキュメントに「index.html」と入力する

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/bc49c7c5-4827-4676-87f7-9524a61d4d1c" width="70%" />

<br><br>

+ 「変更の保存」をクリックする

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/54c4c4c4-f213-487c-9c2f-457756909613" width="70%" />

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/7da1b415-dd08-4a90-9186-a5251d812e0c" width="70%" />

<br><br>

+ 作成したバケットの「アクセス許可」の設定を選択する

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/f854471f-20a2-473c-9323-4ce11da08b23" width="70%" />

<br><br>

+ 「バケットポリシー」の「編集」をクリック

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/62800372-5cef-4bae-a325-d77025d63121" width="70%" />

<br><br>

+ バケットポリシーの「ポリシー」に下記の内容を入力する
  
<br><br>

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::(バケット名)/*"
        }
    ]
}
```

<br><br>

※(バケット名)には作成したバケット名を入力する

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/c60d31ff-03b6-4f71-bde0-57802d1e34f8" width="70%" />

<br><br>

+ ポリシーの記載が完了したら、「変更の保存」をクリックする

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/c4da764c-ddd5-4a49-9b91-7127db407dfd" width="70%" />

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

+ 本GitHubリポジトリからダウンロードした「web」フォルダーをリポジトリに登録する


<br>
GitHubリポジトリ(aws_git_actions_lecture)の「<>Code」から「Download ZIP」をクリックする。

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/b461f977-5928-46d9-8003-e62199d6e15f">


<br>

ダウンロードした「web」フォルダをローカルリポジトリに配置する。

<br>

```
├ .github/
│   └ workflows/
│       └ deploy.yml   #ワークフローファイル
└ web/ ★配置
   ├ index.html
   ├ style.css
   └ img/
```

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/a1572388-45bf-4e4a-82f9-f321751b07b6">

<br>

+ リモートリポジトリにプッシュする

<br>

```
cd (ローカルリポジトリのパス)
git add .
git commit -m "Add GitHubActions Workflow"
git push
```

<br><br>

+ GitHubActionsの実行結果の確認

<br>

GitHubサイトにアクセスして、「Actions」タブに移動して、ワークフローが成功していることを確認する

<br>

→緑のチェックマークが出ていればOK

<br>

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/7e7095f9-c432-494f-aaa8-d555f15b8e42">


<br><br>

+ EC2にデプロイされたサイトを閲覧する

<br>

下記URLにクリックして、デプロイされたWebサイトを確認してみる

<br>

```
http://(EC2のパブリックIPアドレス)
```

<br><br>

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/721782c0-dc80-4d2b-92ad-99762fbca304">


