---

copyright:

  years: 2018

lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}

# Jetbrains IDE 用 IBM Developer Tools
{: #ibm-dev-tools-for-jetbrains}

Jetbrains IDE 用 IBM Developer 拡張機能には、IntelliJ、WebStorm、Android Studio などが含まれ、IDE 内から IDT CLI コマンドに直接アクセスするための新しいメニュー項目が用意されています。これにより、アプリのデプロイメント、{{site.data.keyword.Bluemix_notm}} 上でのアプリの開始/停止/再始動、リモート・アプリ・ログの表示など、Docker と CloudFoundry の両方のワークフローで、エディターのコンテキストを離れることなく、`bx dev` コマンドのサブセットに素早くアクセスすることができます。
{:shortdesc}

![WebStorm IDE 内で実行される IBM Developer Tools の画面キャプチャー。](jetbrains.png "WebStorm IDE 内で実行される IDT メニューの例")

## 従属関係
{: #dependencies}

Jetbrains ベースの IDE 用の IBM Developer Tools 拡張機能を使用するには、[IBM Cloud Developer Tools CLI](index.html) もシステムにインストールされている必要があります。

## インストール
{: #installation}

Jetbrains IDE 用の IBM Developers Tools 拡張機能をインストールする最も簡単な方法は、[IDT Github リポジトリーの jetbrains](https://github.com/IBM-Cloud/ibm-cloud-developer-tools/tree/master/jetbrains) ページにアクセスし、そこにある説明に従うことです。

## 使用量
{: #usage}

開始するにあたって、既存のサーバー・サイド・アプリを使用し、そのアプリを IBM Cloud 対応にすることも、IDT CLI を使用してスターター・キットから新規アプリを作成することもできます (bx dev create)。アプリのプロジェクトが準備できたら、それを JetBrains IDE で開きます。

汎用のサーバー・サイド・アプリがある場合、「ツール」>「IBM Cloud Developer Tools」>「アプリを IBM Cloud 対応にする (Enable app for IBM Cloud)」を選択します。これにより、必要なすべてのファイルがあるかが検査され、欠落しているファイルがあればそれらが追加されます。これらのファイルは、アプリをローカルでビルドできるようにするのに加え、Cloud Foundry アプリを使用する IBM Cloud に、または Kubernetes クラスター内にアプリをデプロイできるようにします。

IDT メニューから基本の build/run/deploy アクションを使用して、クラウド・ネイティブ・アプリを開発します。メニューに含まれていないアクションを実行する必要がある場合は、単純に「Terminal」タブを開き、目的のコマンドを手動で入力してください。

