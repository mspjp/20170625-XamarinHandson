# Xamarin with Azure Mobile Apps ハンズオン (Windows)

このハンズオンでは、Visual Studio を使用して、Azure Mobile Apps と Xamarin を組み合わせたモバイルアプリの開発を行います。

## 1. 前提環境

 - Visual Studio 2017 がインストールされた Windows PC
 - Microsoft Imagine が使用可能な Microsoft アカウント

## 2. Visual Studio の設定

Azure へのアクセスを行うため、Visual Studio の画面の右上の **サインイン** をクリックし、Microsoft アカウントを使用してログインして下さい。

|1|
|--|
|<img src="img-windows/1.png?raw=true" max-width="320px">|

1. サインイン をクリック

|2|
|--|
|<img src="img-windows/2.png?raw=true" max-width="320px">|

2. Imagine が登録されているMicrosoft アカウントでログイン

|3|
|--|
|<img src="img-windows/3.png?raw=true" max-width="320px">|

3. アカウント名が表示されればOK

## 3. プロジェクトの作成

Azure Mobile Apps を使用する Xamarin.Forms のプロジェクトを作成します。

ツールバーより **ファイル** → **新規作成** → **プロジェクト** と選択して下さい。

|4|
|--|
|<img src="img-windows/4.png?raw=true" max-width="320px">|

左ペインを **インストール済み** → **テンプレート** → **Visual C#** → **Cross-Platform** の順番で開き、右ペイン内の **Cross Platform App (Xamarin)** を選択して下さい。

|5|
|--|
|<img src="img-windows/5.png?raw=true" max-width="320px">|

ダイアログ下部の **名前** を任意の名前に変更し、**OK** をクリックします。

|6|
|--|
|<img src="img-windows/6.png?raw=true" max-width="320px">|

次に表示されるダイアログでは、作成する Xamarin のプロジェクトの初期設定を決めることができます。

それぞれの選択は以下のようにプロジェクトに反映されます。

> 
> - テンプレートの選択
>   - 空のアプリ：空の画面が1つだけ存在するプロジェクト
>   - マスター/詳細：リストが表示されるマスターページと、リスト内のアイテムを選択したときに表示される詳細ページが用意されているプロジェクト
>- UI テクノロジ
>   - Xamarin.Forms：Xamarin.Forms を使用し、UI 部分の設計を Xaml などを用いて開発できる
>   - ネイティブ：プラットフォームごとに UI 部分の設計を個別に行う
>- コード共有方法
>   - 共有プロジェクト：ShardProjectによるコード共有を行う。`#if` ディレクティブなどを使用できる。
>   - ポータブルクラスライブラリ（PCL）：PCLを使用してコード共有を行う。共有部分に Nuget のライブラリの参照を追加できる。
>- Microsoft Azure
>    - クラウド内のホスト：テンプレートを **マスター/詳細** にした時のみ選択可能。Azure Mobile Apps を使用した MBaas を実現できる。

今回のハンズオンでは、**マスター/詳細・Xamarin.Forms・共有プロジェクト・クラウド内のホスト にチェック** の状態にしてください。

選択したら **OK** をクリックします。

次の画面では、Azure へホスティングする Mobile Apps バックエンドの構成などを入力します。

|8|
|--|
|<img src="img-windows/8.png?raw=true" max-width="320px">|

**Mobile App の名前** の欄に任意の名前を入力して下さい。
（これがAzure上での App Service の名前になります。）

### 3.1 リソースグループの作成

**リソースグループ** の右の **新規作成** をクリックします。

|9|
|--|
|<img src="img-windows/9.png?raw=true" max-width="320px">|

任意の名前（先程の **Mobile App の名前** と同じだとわかりやすい）を入力し、**OK** をクリックします。

> **リソースグループ**
>
> Azure 上で管理するリソースに対して、同一用途のものなどを1つにまとめて管理できる仕組み。
> すべてのリソースはいずれかのリソースグループに所属している。
> 複数の仮想マシンを使用している場合などに有効的に活用できる。

### 3.2 App Service の作成

**App Service プラン** の右の **新規作成** をクリックします。

|10|
|--|
|<img src="img-windows/10.png?raw=true" max-width="320px">|

**App Service プラン** に任意の名前（先程の **Mobile App の名前** と同じだとわかりやすい）を入力します。

**場所** を **Japan East**、**サイズ** を **無料** にした上で、 **OK** をクリックします。

入力が終わったら **作成** をクリックします。

Azure へのデプロイが行われるので、しばらく待機します。

|11|
|--|
|<img src="img-windows/11.png?raw=true" max-width="320px">|

デプロイが完了すると、Xamarin.Forms のプロジェクト及び Mobile App Service のプロジェクトが作成されます。

UWPに関するダイアログが表示された場合は **OK** をクリックしてください。

|12|
|--|
|<img src="img-windows/12.png?raw=true" max-width="320px">|

パッケージの復元が行われるので、しばらく待機します。

## 4. 実行してみる

### 4.1 Mobile App Service プロジェクトのデプロイ

ソリューションエクスプローラーから、**[プロジェクト名].MobileAppService** を右クリックし、**公開** をクリックします。

|13|
|--|
|<img src="img-windows/13.png?raw=true" max-width="320px">|

中央に表示される画面で **Microsoft Azure App Service(A)** を選択し、**既存のものを選択** を選択した上で **発行** をクリックします。

|14|
|--|
|<img src="img-windows/14.png?raw=true" max-width="320px">|

表示さてたダイアログから、先程作成した App Service を選択し、**OK** をクリックします。

しばらく待機すると自動でブラウザが開き、以下のようなページが表示されます。

|15|
|--|
|<img src="img-windows/15.png?raw=true" max-width="320px">|

これで、デプロイは完了です。

**※このサイトのアドレスは後で使用するので、タブを閉じないでおくか、URLをメモしてください。**

以降、デプロイを再度おこなう場合は、プロジェクトを右クリックして **公開** をクリックした画面で、 **発行** をクリックすればOKです。

|16|
|--|
|<img src="img-windows/16.png?raw=true" max-width="320px">|

### 4.2 Android プロジェクトの実行

Visual Studio の画面上部で、**[プロジェクト名].Android** が選択されていることを確認し、右の▶をクリックしてください。

|17|
|--|
|<img src="img-windows/17.png?raw=true" max-width="320px">|

Android 上でアプリが立ち上がれば成功です。

|18|
|--|
|<img src="img-windows/18.png?raw=true" max-width="320px">|

### 4.3 Android アプリを動かしてみる

**NOT NOW** を選択し、次の画面でツールバー上の **ADD ITEM** をタップします。

|19|
|--|
|<img src="img-windows/19.png?raw=true" max-width="320px">|

アイテムの入力画面が開くので、**SAVE** をクリックします。

|20|
|--|
|<img src="img-windows/20.png?raw=true" max-width="320px">|

元の画面のリストに、追加したアイテムが表示されていればOKです。

|21|
|--|
|<img src="img-windows/21.png?raw=true" max-width="320px">|

## 5. 認証を行う

Azure App Service では、OAuth などを使用した認証を簡単に追加することができます。

このハンズオンでは、Microsoft アカウントを使用して認証を行う手順を紹介します。

### 5.1 Azure への登録 - 1

はじめに、Azure ポータルを開きます。

[https://portal.azure.com/](https://portal.azure.com/)

ポータル内から、前の章で作成した App Service を開きます。

ページ左のリストから **App Service** をクリックします。

|22|
|--|
|<img src="img-windows/22.png?raw=true" max-width="320px">|

リスト内から前の章で入力した名前をクリックします。

|23|
|--|
|<img src="img-windows/23.png?raw=true" max-width="320px">|

画面右側に選択した App Service の情報が表示されるので、左下にある **認証/承認** をクリックします。

|24|
|--|
|<img src="img-windows/24.png?raw=true" max-width="320px">|

切り替わった画面で、 **App Service 認証** を **オン** に切り替えます

|25|
|--|
|<img src="img-windows/25.png?raw=true" max-width="320px">|

**要求が認証されない場合に実行するアクション** を **Microsoft アカウントでのログイン** に変更し、下部の Microsoft の **構成されていません** の部分をクリックします。

### 5.2 アプリケーションの登録

ここで、ブラウザで新しいタブを開き、以下のアドレスへアクセスします。

[https://apps.dev.microsoft.com/?mkt=ja-jp#/appList](https://apps.dev.microsoft.com/?mkt=ja-jp#/appList)

|26|
|--|
|<img src="img-windows/26.png?raw=true" max-width="320px">|

ここでは、Microsoft アカウントで認証を行うためのアプリケーションの作成を行います。

ページ右上の **アプリの追加** をクリックします。

|27|
|--|
|<img src="img-windows/27.png?raw=true" max-width="320px">|

**Application Name** を入力し、**Create** をクリックします。

|28|
|--|
|<img src="img-windows/28.png?raw=true" max-width="320px">|

表示されている情報の中の、**アプリケーションID** をメモします。

次に、**プラットフォームの追加** をクリックします。

|29|
|--|
|<img src="img-windows/29.png?raw=true" max-width="320px">|

出てくる画面では **Web** を選択してください。

|30|
|--|
|<img src="img-windows/30.png?raw=true" max-width="320px">|

**リダイレクト URL** に以下の規則で入力してください。

**[デプロイ時に自動でブラウザが開いたときのURL（https始まり）]/.auth/login/microsoftaccount/callback**

> 例）https://amahandson20170624041541.azurewebsites.net/.auth/login/microsoftaccount/callback

次に、**新しいパスワードの生成** をクリックします。

|31|
|--|
|<img src="img-windows/31.png?raw=true" max-width="320px">|

画面上にパスワードが表示されるので、メモした上で **OK** をクリックしてください。

ページ下部の **保存** をクリックし、変更を保存します。

### 5.3 Azure への登録 - 2

Azure ポータルに戻り、**Microsoft アカウントの認証設定** の **クライアントID** と **クライアントシークレット** にそれぞれ先程のページで表示された **アプリケーションID** と **パスワード** を貼り付けます。

|32|
|--|
|<img src="img-windows/32.png?raw=true" max-width="320px">|

入力が終わったら、下部の **OK** をクリックします。

**認証/承認** の画面に戻るので、上部の **保存** をクリックします。

### 5.4 App Service プロジェクトへの実装

Visual Studio に戻ります。

|33|
|--|
|<img src="img-windows/33.png?raw=true" max-width="320px">|

はじめに、ソリューションエクスプローラーから、**[プロジェクト名].MobileAppService** プロジェクトの **Controller** → **ItemController.cs** を開きます。

`namespace` 直下にある `[Authorize]` のコメントアウトを外します。

```diff
 namespace AMAHandson.MobileAppService.Controllers
 {
     // TODO: Uncomment [Authorize] attribute to require user be authenticated to access Item(s).
-    // [Authorize]
+    [Authorize]
     public class ItemController : TableController<Item>
     {
```

ファイルを保存した上で、先程の手順と同じようにデプロイを行います。

この `Authorize` アトリビュートを追加することで、このクラスのメソッドなどへのアクセスには、認証が必要になります。

> メソッドに対してアトリビュートをつけることで、そのメソッドだけに認証をかけることもできます。 

### 5.5 Xamarin.Forms アプリへの実装

次に、ソリューションエクスプローラーから、**[プロジェクト名]** プロジェクトを開き、**Services** → **AzureDataStore.cs** を開きます。

|34|
|--|
|<img src="img-windows/34.png?raw=true" max-width="320px">|

`AzureDataStore` クラスの定義の直下にあるプロパティ **UseAuthentication** と **AuthProvider** を以下のように書き換えます。

```diff
 	public class AzureDataStore : IDataStore<Item>
 	{
-         public bool UseAuthentication => false;
-         public MobileServiceAuthenticationProvider AuthProvider => MobileServiceAuthenticationProvider.Facebook;
+         public bool UseAuthentication => true;
+         public MobileServiceAuthenticationProvider AuthProvider => MobileServiceAuthenticationProvider.MicrosoftAccount;

         bool isInitialized;
```

変更が終わったら、ファイルを保存しビルド及び実行します。

起動時の画面で **SIGN IN** を選択すると Microsoft アカウントのサインイン画面に遷移します。


|35|
|--|
|<img src="img-windows/35.png?raw=true" max-width="320px">|

Microsoft アカウントへのログインに成功すると、作成したアプリケーションとの連携許可の画面が表示されるので、**はい** をクリックします。

|36|
|--|
|<img src="img-windows/36.png?raw=true" max-width="320px">|

# 6. API を追加してみる

この章では、App Service に新しい API エンドポイントを追加し、Xamarin.Forms アプリから呼び出すまでを行います。

# 6.1. App Service に API を追加

はじめに、ソリューションエクスプローラーから、**[プロジェクト名].MobileAppService** プロジェクトの **Controller** を右クリックし、**追加** → **コントローラー** を選択します。

|37|
|--|
|<img src="img-windows/37.png?raw=true" max-width="320px">|

ダイアログでは **Web API 2 コントローラー - 空** を選択します。

|38|
|--|
|<img src="img-windows/38.png?raw=true" max-width="320px">|

名前の入力では、**TimeController** と入力します。

|39|
|--|
|<img src="img-windows/39.png?raw=true" max-width="320px">|

生成された **TimeController** クラスに以下の using を追加します。

```cs
using Microsoft.Azure.Mobile.Server.Config;
```

また、**TimeController** クラスの定義部に、以下のアトリビュートを付けます。

```cs
[MobileAppController]
```

ここまでで、以下のようになっていればOKです。

```TimeController.cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Net;
using System.Net.Http;
using System.Web.Http;
using Microsoft.Azure.Mobile.Server.Config;

namespace AMAHandson.MobileAppService.Controllers
{
    [MobileAppController]
    public class TimeController : ApiController
    {
    }
}
```

次に、作成する API のサンプルとして、現在時刻を返すような API を作成します。

クラス内に、以下のメソッドを追加します。

```cs
[HttpGet, Route("now")]
public string Get()
{
    var dt = DateTime.Now;
    return dt.ToString("yyyy/MM/dd HH:mm:ss");
}
```

次に、作成した API が読み込まれるようにします。

ソリューションエクスプローラーから、**[プロジェクト名].MobileAppService** プロジェクトの **App_Start** → **Startup.MobileApp.cs** を開きます。

`ConfigureMobileApp` メソッド内の `new MobileAppConfiguration()` を呼び出している部分を以下のように変更します。

```diff
 new MobileAppConfiguration()
     .UseDefaultConfiguration()
+    .MapApiControllers()
     .ApplyTo(config);
```

ここまで完了したら、 App Service プロジェクトをデプロイします。

次に、Azure Portal を開き、App Service を開きます。

|40|
|--|
|<img src="img-windows/40.png?raw=true" max-width="320px">|

左サイドメニューから **アプリケーション設定** を開きます。

|41|
|--|
|<img src="img-windows/41.png?raw=true" max-width="320px">|

右ペインの中にある **アプリ設定** の項目に以下のキーと値を追加します

```
キー：MS_SkipVersionCheck
値：true
```

完了したら、上部の **保存** をクリックします。

### 6.2. Xamarin.Forms から追加した API を叩く

App Service 側に API を追加したので、Xamarin.Forms 側から呼び出すコードを書いていきます。

呼び出すタイミングは、「Aboutページに新しく追加したボタンをクリックしたら」にし、結果をラベルに表示させます。

ソリューションエクスプローラーから、**[プロジェクト名]** プロジェクトの **Services** → **IDataStore.cs** を開きます。

`IDataStore` クラスに新しく以下の抽象メソッドを追加します。

```cs
Task<string> GetCurrentTimeAsync();
```

ソリューションエクスプローラーから、**[プロジェクト名]** プロジェクトの **Services** → **AzureDataStore.cs** を開きます。

`AzureDataStore` クラスに新しく以下のメソッドを追加します。

```cs
public async Task<string> GetCurrentTimeAsync()
{
    await InitializeAsync();
    return await MobileService.InvokeApiAsync<string>("Time/now");
}
```

ソリューションエクスプローラーから、**[プロジェクト名]** プロジェクトの **Services** → **MockDataStore.cs** を開きます。

> このクラスは、モック用のクラスなのでハンズオン中に使用することはありませんが、メソッドの実装が必要なため編集します。

`MockDataStore` クラスに新しく以下のメソッドを追加します。

```cs
public async Task<string> GetCurrentTimeAsync()
{
    await InitializeAsync();
    return await Task.FromResult(DateTime.Now.ToString("yyyy/MM/dd/ HH:mm:ss"));
}
```

ソリューションエクスプローラーから、**[プロジェクト名]** プロジェクトの **ViewModels** → **AboutViewModel.cs** を開きます。

> Xamarin.Forms では一般的に MVVM (Model-View-ViewModel) アーキテクチャが用いられます。

`AboutViewModel` クラスに新しく以下のプロパティを追加します。

```cs
public string Time { get; private set; }
public ICommand GetTimeCommand { get; }
```

また、コンストラクタ内の最後に以下のコードを追加します。

```cs
Time = "unknown";
GetTimeCommand = new Command(async () =>
{
    Time = await DataStore.GetCurrentTimeAsync();
});
```

ソリューションエクスプローラーから、**[プロジェクト名]** プロジェクトの **Views** → **AboutPage.xaml** を開きます。

64-65行目に以下のコードを挿入します。

```xaml
<Button Margin="0,10,0,0"
        Text="Get time" 
        Command="{Binding GetTimeCommand}"
        BackgroundColor="{StaticResource Primary}"
        TextColor="White"/>
<Label  Text="{Binding Time}"
        TextColor="Black"/>
```

以下の場所に挿入となります。

```diff
         <Button Margin="0,10,0,0"
                 Text="Learn more" 
                 Command="{Binding OpenWebCommand}"
                 BackgroundColor="{StaticResource Primary}"
                 TextColor="White"/>
+        <Button Margin="0,10,0,0"
+                Text="Get time" 
+                Command="{Binding GetTimeCommand}"
+                BackgroundColor="{StaticResource Primary}"
+                TextColor="White"/>
+        <Label  Text="{Binding Time}"
+                TextColor="Black"/>
       </StackLayout>
     </ScrollView>
   </Grid>
 </ContentPage>
```

|42|
|--|
|<img src="img-windows/42.png?raw=true" max-width="320px">|

このように、About ページに **GET TIME** ボタンが追加され、タップすると現在の時刻が表示されていればOKです。