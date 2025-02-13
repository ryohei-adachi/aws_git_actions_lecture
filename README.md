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
