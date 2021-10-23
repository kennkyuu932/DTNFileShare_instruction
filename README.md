# DTNFileShareの使い方

## PlayStore等からIBR-DTN,Slackのインストール
下記リンクのアプリをそれぞれダウンロード.

IBR-DTN:
[https://play.google.com/store/apps/details?id=de.tubs.ibr.dtn](https://play.google.com/store/apps/details?id=de.tubs.ibr.dtn)

Slack:
[https://play.google.com/store/apps/details?id=com.Slack](https://play.google.com/store/apps/details?id=com.Slack)

## Slack APPサーバを作成
- glitchを使用

下記リンクからプロジェクトをRemixする.

`https://(プロジェクト名).glitch.me` が以降で使用するサーバのURLとなる.

(例)プロジェクト名がfoo-test-hogeである時,サーバのURLは `https://foo-test-hoge.glitch.me` となる.

- glitchを使用しないとき

下記リンクからプロジェクトをダウンロードする.

index.jsを実行して外部に,URLを公開する.

そのURLが以降で使用するサーバのURLとなる.

slack-dtn-testのプロジェクトリンク:
[https://glitch.com/edit/#!/slack-dtn-test](https://glitch.com/edit/#!/slack-dtn-test)

## Slack APPを作成
下記リンク(SlackAPI Applications)からSlack APPを作成する.

OAth & Permissionでの設定で使用するScopesは,Bot Token Scopesの以下の5つ.
- chat:write
- groups:write
- im:write
- mpim:write
- users:read

App Homeの設定でHome Tabを有効にしておく.

Event Subscription設定でRequest URLの入力で作成したSlack AppサーバのURL+/eventsを入力.

(例)Slack AppサーバのURLが `https://foo-test-hoge.glitch.me` である時,
Request URLに入力するURLは, `https://foo-test-hoge.glitch.me/events` とする.

Interactivity & Shortcuts設定でも上記と同様に,Request URLの入力で作成したSlack AppサーバのURL+/actionsを入力.

(例)Slack AppサーバのURLが `https://foo-test-hoge.glitch.me` である時,
Request URLに入力するURLは, `https://foo-test-hoge.glitch.me/actions` とする.

アプリをワークスペースにインストールする.

この時に表示されるBot User OAuth Tokenをコピーして作成したサーバの.envファイルのSLACK_BOT_TOKENの値に書き込む.

またBasic Information設定でsigning secretを作成したサーバの.envファイルのSLACK_SIGNING_SECRETの値に書き込む.

SlackAPI Applications:
[https://api.slack.com/apps?new_app](https://api.slack.com/apps?new_app)

## DTNFileShareをビルド,実機にインストール

Android Studio 4.1.3を使用.

下記リンクからDTNFileShareのプロジェクトをダウンロードしてAndroid Studioでappフォルダに関して開く.

/app/scr/main/java/de/tub/ibr/dtn/sharebox/SendSlackMessage.javaの変数SLACK_APP_TOKENに作成したSlack appのBot User OAuth Token の文字列を入力.

/app/scr/main/java/de/tub/ibr/dtn/sharebox/SendSlackMessage.javaの変数SLACK_APP_URLにglitch等で作成したサーバーのURLを入力.

/app/scr/main/java/de/tub/ibr/dtn/sharebox/RegisterEIDActivity.javaの変数SLACK_APP_URLにglitch等で作成したサーバーのURLを入力.

ビルドして実機にインストールする.

DTNFileShareのプロジェクト
[https://github.com/kennkyuu932/Share](https://github.com/kennkyuu932/Share)
