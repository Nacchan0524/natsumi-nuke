# natsumi-nuke
For AWS Nuke

AWS Nukeというオープンソースのツールを実行するためのワークフローファイルと定義ファイル(nuke-configファイル)です。

nuke-workflow.yaml:

  ・runs-on: の部分はOrganizationsのランナーに変えて使用してください。
  
  ・GitHub内のvar変数にIAM_ARNとしてGitHub ActionsのAWSへのアクセスに使用するIAMロールのarnを設定してください。

  ・.github/workflows/nuke-workflow.yamlにファイルを保存してください

  ・このファイルでは、「Configure AWS credentials」ジョブでAWSにアクセス→
  「Install AWS Nuke」ジョブで任意のバージョンのNukeをインストール→
  「Run aws-nuke」ジョブでNukeを実行→
  「Save output from aws-nuke」ジョブでNuke実行結果を成形して保存→
  「Send output to Slack」ジョブでslackに送信するメッセージを作成→
  「Send message to Slack」ジョブで実際にslackへ送信　
  という流れで処理が進んでいます。

nuke-config.yml

  ・NukeのGitHubリポジトリ： https://github.com/ekristen/aws-nuke
  ・Nukeで実際に削除するリソースを指定しています
