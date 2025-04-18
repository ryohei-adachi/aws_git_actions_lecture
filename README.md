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


<br><br>

```
git push origin mianで、下記のエラーが発生した場合、「git remote add origin (GitリポジトリURL).git」の登録が誤っている可能性があります。

fatal:'(登録したURL)' does not appear to be a git repository
fatal: Cloud not read from remote repository

Please make sure you have the correct access rights
and the repository exits.


・まず、既存のoriginのURLが正しいか確認しましょう

git remote -v

・誤って登録されていた場合、既存のoriginを削除して登録し直しましょう
git remote remove origin
git remote add origin https://github.com/(ユーザ名)/(リポジトリ名).git

```

# ② AWSの設定

<br>

+ AWSにログインする。

<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/4c8cec3b-b46a-4e04-a90c-f5378e9f63a6" width="70%" />

<br><br>

+ AWSのマジメントコンソールを開き、リージョンを選択する
  + 本手順書では、「東京」リージョンに選択したうえで進める。

<br><br>




<img src="https://github.com/ryohei-adachi/aws_lecture/assets/75190594/a5490b76-9d0d-4306-a100-3adc8b9fc3b4" width="70%" />

<br>

## S3バケットの構築

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

<img src="https://github.com/user-attachments/assets/dfb63323-5436-4af8-a813-eb19ac48b605" width="70%" />


<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/f46a6745-6d91-4101-8711-b77bfd3e4586" width="70%" />

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/abed2e67-9b69-4fd3-af1e-c50863840f2a" width="70%" />

<br><br>
上記以外の項目は、変更なしで、「バケットの作成」をクリックする

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/0f5bcebb-a4cc-428c-8883-d505a1a232f2" width="70%" />

<br><br>

<img src="https://github.com/user-attachments/assets/4e08c25f-41bc-479b-9584-af6bd228df07" width="70%" />



<br><br>

+ 作成したバケットを選択して、「プロパティ」を選択する

<br><br>

<img src="https://github.com/user-attachments/assets/1e06a82b-40d4-4d1b-86ea-a55b351a5827" width="70%" />

<br><br>

+ 一番下にある「静的ウェブサイトホスティング」の編集ボタンをクリックする

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/3b211eb9-8fb9-48dd-a91b-3bb2df5b2136" width="70%" />

<br><br>

+ 「静的ウェブサイトホスティングを編集」において、静的ウェブサイトホスティングを「有効」にする

<br><br>

<img src="https://github.com/user-attachments/assets/eb14f079-33a1-4d6d-89c3-76e9aa80de91" width="70%" />

<br><br>

+ インデックスドキュメントに「index.html」と入力する

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/bc49c7c5-4827-4676-87f7-9524a61d4d1c" width="70%" />

<br><br>

+ 「変更の保存」をクリックする

<br><br>

<img src="https://github.com/ryohei-adachi/aws_lectureaws_lecture2/assets/75190594/54c4c4c4-f213-487c-9c2f-457756909613" width="70%" />

<br><br>

<img src="https://github.com/user-attachments/assets/cae057fc-cf03-48ad-a12b-8ea365247d48" width="70%" />



<br><br>

+ 作成したバケットの「アクセス許可」の設定を選択する

<br><br>

<img src="https://github.com/user-attachments/assets/89841a78-9d40-4ce9-9ce6-3a68d4dd50cb" width="70%" />

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

<img src="https://github.com/user-attachments/assets/c168998f-61e2-48a9-8bcc-5cfa1737ef21" width="70%" />


<br><br>

+ ポリシーの記載が完了したら、「変更の保存」をクリックする

<br><br>

<img src="https://github.com/user-attachments/assets/e3ef4f20-115a-4fe2-a5c4-c088a40969b2" width="70%" />


<br><br>

<br>

## IAMの作成

<br>

+ AWSの検索ボックスに、IAMと入力し、IAMサービスに移動する

<br>

<img src="https://github.com/user-attachments/assets/61d70580-3772-444d-b74f-693435045c32" width="70%" />

<br>

+ 左メニューのユーザーを選択する

<br>

<img src="https://github.com/user-attachments/assets/0cecfd09-0662-41b1-b63c-7bfc8b14df45" width="70%" />

<br>

+ 「ユーザーの作成」ボタンをクリックする

<br>
  
<img src="https://github.com/user-attachments/assets/fc509396-679c-4fa1-8094-f601a528f586" width="70%" />

<br>

<img src="https://github.com/user-attachments/assets/c440dd56-1593-4bd1-b4dd-3b9c5b126021" width="70%" />

<br>

<img src="https://github.com/user-attachments/assets/066bb94f-c5f1-4272-b664-7e606f7329e1" width="70%" />

<br>

<img src="https://github.com/user-attachments/assets/9d107c05-44aa-4193-9d08-f4aad05c3e52" width="70%" />

<br>

<img src="https://github.com/user-attachments/assets/d05f7884-aa00-45f6-8187-4370a00df18e" width="70%" />

<br>

<img src="https://github.com/user-attachments/assets/cea737be-e202-4ed4-9625-9e1fe086ab64" width="70%" />

<br>

<img src="https://github.com/user-attachments/assets/99377fb0-b647-498f-a3c4-129bb076de35" width="70%" />

<br>

<img src="https://github.com/user-attachments/assets/f8e7bb9d-195e-407b-9ea2-2aac0d92f4ae" width="70%" />

<br>

<img src="https://github.com/user-attachments/assets/08e957d2-e96c-43b2-8698-a693ee72f3ee" width="70%" />

<br>

<img src="https://github.com/user-attachments/assets/ca053598-de30-4da9-bbc6-e7b3af91fe82" width="70%" />

<br>

<img src="https://github.com/user-attachments/assets/1927c540-32f9-4bed-bc39-f14b59aadf5c" width="70%" />

<br>

<img src="https://github.com/user-attachments/assets/4d06565d-1a56-4796-8633-50015d3cbfac" width="70%" />

<br>
<img src="https://github.com/user-attachments/assets/25a29413-0512-4cb0-9c22-94808c17324b" width="70%" />



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
| AWS_ACCESS_KEY_ID | 作成したIAMのアクセスキー |
| AWS_SECRET_SCCESS_KEY | 作成したIAMのシークレットキー |
| S3_BUCKET_NAME | 作成したS3のバケット名 |



<br>

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/c8026284-58c2-4a95-b4ef-6b7caf5f3566">


<br>


<img width="70%" alt="image" src="https://github.com/user-attachments/assets/e4a5539c-f67a-440b-ae43-30cb6ce94489">

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
name: Deploy to AWS S3 Host
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

      - name: AWS認証
        uses: aws-actions/configure-aws-credentials@v3
        with:
           aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
           aws-secret-access-key: ${{ secrets.AWS_SECRET_SCCESS_KEY }}
           aws-region: ap-northeast-1 #東京リージョンを指定
        
      - name: S3にアップロード
        run:
          aws s3 sync ./web/ s3://${{ secrets.S3_BUCKET_NAME }}/ --delete
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

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/20e474d8-9e73-4e8f-8ff0-9c42dcf32e3f">


<br><br>

+ S3にデプロイされたサイトを閲覧する

<br>

再びバケットの「プロパティ」タブを開き、「静的ウェブホスティング」のバケットウェブサイトエンドポイントURLを確認する


<br>

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/33073971-eead-4899-a4b0-890941bef08f">

<br>

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/aabfbc1e-2a93-440d-9cbe-b99381c62908">



<br>

```
http://(バケット名).s3-website-ap-northeast-1.amazonaws.com
```

<br>

デプロイされたサイトが確認できる

<br><br>

<img width="70%" alt="image" src="https://github.com/user-attachments/assets/81bab87d-130c-4e16-a0dd-4087f649d1c9">


