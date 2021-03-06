---
title: Intune で管理されている iOS および Mac OS X デバイスの構成項目を作成する
titleSuffix: Configuration Manager
description: System Center Configuration Manager の iOS および Mac OS X 構成項目使用して、iOS デバイスと Mac OS X デバイスの設定を管理します。
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 613a48ac-c55d-4c4a-94ea-d3747a1b10cb
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0a6925cdc1f3b3a5018cc4895820019d88254bd3
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32353343"
---
# <a name="how-to-create-configuration-items-for-ios-and-mac-os-x-devices-managed-with-intune"></a>Intune で管理されている iOS および Mac OS X デバイスの構成項目を作成する方法
System Center Configuration Manager の **iOS および Mac OS X** 構成項目を使用して、Microsoft Intune に登録されているか、Configuration Manager によってオンプレミスで管理されている iOS デバイスと Mac OS X デバイスの設定を管理します。  
  
### <a name="to-create-an-ios-and-mac-os-x-configuration-item"></a>iOS および Mac OS X 構成項目を作成するには  
  
1.  Configuration Manager コンソールで、**[資産とコンプライアンス]** をクリックします。  
  
2.  **[資産とコンプライアンス]** ワークスペースで **[コンプライアンス設定]** を展開して、**[構成項目]** をクリックします。  
  
3.  **[ホーム]** タブの **[作成]** グループで、**[構成項目の作成]** をクリックします。  
  
4.  **構成項目の作成ウィザード** の **[全般]** ページで、構成項目の名前と、必要に応じて説明を入力します。  
  
5.  **[作成する構成項目の種類の指定]** で、 **[iOS および Mac OS X]** を選択します。  
  
6.  Configuration Manager コンソールで構成項目を検索およびフィルター処理するのに役立つカテゴリを作成して割り当てる場合は、**[カテゴリ]** をクリックします。  
  
7.  ウィザードの **[サポートされているプラットフォーム]** ページで、構成項目を評価する特定の iOS または Mac OS X プラットフォームを選択します。  
  
8.  ウィザードの **[デバイスの設定]** ページで、構成する設定グループを選択します。 このトピックの「 [iOS と Mac OS X の構成項目設定のリファレンス](#BKMK_Setref) 」で詳細情報を確認し、 **[次へ]** をクリックします。  
  
    > [!TIP]  
    >  必要な設定が一覧にない場合は、 **[既定の設定グループに含まれない追加の設定を構成する]** チェック ボックスをオンにします。  
  
9. 各設定ページで、必要な設定と、その設定がデバイスに対応していないときにその設定を修正するかどうかを構成します (これがサポートされている場合)。  
  
10. 設定グループごとに、構成項目が非対応であることが検出されたときに報告される重要度を構成することもできます。  
  
    -   **なし** - このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に非対応重要度を何も報告しません。  
  
    -   **情報** - このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に**情報**というレベルで非対応重要度を報告します。  
  
    -   **警告** - このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に**警告**というレベルで非対応重要度を報告します。  
  
    -   **重大** - このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に**重大**というレベルで非対応重要度を報告します。  
  
    -   **重大 (イベント)** - このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に**重大**というレベルで非対応重要度を報告します。 重要度のレベルは、アプリケーションのイベント ログでも Windows のイベントとしてログが登録されます。  
  
11. ウィザードの **[プラットフォームの適用性]** ページで、前に選択したサポート対象プラットフォームと互換性がないすべての設定を確認します。 前に戻ってこれらの設定を削除するか、操作を続行できます。  
  
    > [!TIP]  
    >  サポートされていない設定のコンプライアンスは評価されません。  
  
12. ウィザードを完了します。  
  
 新しい構成項目は、 **[資産とコンプライアンス]** ワークスペースの **[構成項目]** ノードに表示されます。  
  
##  <a name="ios-and-mac-os-x-configuration-item-settings-reference"></a>iOS と Mac OS X の構成項目設定のリファレンス  
  
###  <a name="password"></a>パスワード  
  
|設定の名前|詳細|  
|------------------|-------------|  
|**モバイル デバイスのパスワードの設定が必要**|サポート対象デバイスのパスワードが必要です。|  
|**パスワードの最小文字数**|パスワードの最小の長さ。|  
|**パスワードの有効期限 (日数)**|パスワードの変更が必要になるまでの日数。|  
|**記憶するパスワードの数**|以前に使用したパスワードを再利用できないようにします。|  
|**デバイスをワイプするまでのログオン失敗回数**|ログインの試みがこの回数だけ失敗した場合は、デバイスがワイプされます。<br /><br /> (iOS のみ)|  
|**パスワードの複雑さ**|「1234」などの PIN を指定できるのか、または強力なパスワードを指定する必要があるのかを選択します。| 
|**単純なパスワードを許可する**|**0000** や **1234** のような単純なパスワードを許可します。|
|**ロック解除用の指紋**|指紋を使用してデバイスのロックを解除できるようにします。|
|**パスコードの変更** (監視モードのみ)|デバイスのパスワードの追加、変更、または削除を許可します。|
  
###  <a name="device"></a>デバイス  
 これらの設定は、iOS と Mac OS X のどちらのデバイスにも適用されます。  
  
|設定の名前|詳細|  
|------------------|-------------|  
|**Game Center の友達の追加**|Game Center アプリで友達を追加できるようにします。|
|**音声ダイヤル**|デバイスの音声ダイヤル機能を使用できるようにします。|  
|**音声アシスタント**|Siri のような音声アシスタント アプリを使用できるようにします。|  
|**ロック中の音声アシスタント**|デバイスがロックされているときに Siri のような音声アシスタント アプリを使用できるようにします。|  
|**画面の取り込み**|デバイスのディスプレイのスクリーン ショットを取得できるようにします。|  
|**ビデオ チャット クライアント**|Facetime などのビデオ チャット アプリを使用できるようにします。|  
|**マルチプレーヤー ゲーム**|インターネット上の他のプレーヤーとゲームをプレイできるようにします。|  
|**ロック中のパーソナル ウォレット ソフトウェア**|Passbook のようなパーソナル ウォレット ソフトウェアを使用できるようにします。|  
|**診断データの送信**|アプリのログ ファイルを送信できるようにします。|  
|**アクション センターの通知**|ユーザーに、デバイスのロックを解除せずに通知ビューにアクセスすることを許可します。|
|**Apple Music** (監視モードのみ)|Apple Music アプリの使用を許可します。|
|**ポッドキャスト** (監視モードのみ)|ポッドキャスト アプリの使用を許可します。|
|**メッセージ アプリ** (監視モードのみ)|メッセージ アプリを使ったテキスト メッセージの送信を許可します。|
|**壁紙の変更** (監視モードのみ)|ユーザーにデバイスの壁紙の変更を許可します。|
|**単語の定義の検索** (監視モードのみ)|単語を強調表示し、その定義を検索できる iOS 機能の使用を許可します。|
|**ペアリングされている Apple Watch の手首検出**|有効にすると、Apple Watch が装着されていないときには Apple Watch に通知が表示されません。|
|**Siri の不適切な単語フィルター** (監視モードのみ)|Siri が不適切な言葉をディクテーションまたは読み上げないようにします。|
|**デバイス名の変更** (監視モードのみ)|ユーザーがデバイスの名前を変更することを許可します。|
|**診断の送信の設定変更** (監視モードのみ)|デバイスから Apple への診断データの送信を許可またはブロックします。|
|**Game Center** (監視モードのみ)|Game Center アプリの使用を許可します。|
|**iTunes Radio** (監視モードのみ)|iTunes Radio アプリの使用を許可します。|
|**Apple News** (監視モードのみ)|Apple News アプリの使用を許可します。|
|**Apple Watch のペアリング** (監視モードのみ)|デバイスと Apple Watch とのペアリングを許可します。|
|**自動修正** (監視モードのみ)|デバイスで自動的にスペル ミスの単語が修正されるようにします。|
|**Bluetooth の変更** (監視モードのみ)|ユーザーにデバイスでの Bluetooth の設定の変更を許可します。|
|**アプリの携帯データ ネットワークの使用設定に対する変更** (監視モードのみ)|携帯データ ネットワークの使用が許可されているアプリをユーザーが管理することを許可します。|
|**キーボード ショートカット** (監視モードのみ)|キーボード ショートカットを使用できるようにします。|
|**予測表示キーボード** (監視モードのみ)|予測表示キーボードを使用して、ユーザーが入力していると思われる単語の提案を許可します。|
|**キーボード スペル チェック** (監視モードのみ)|デバイスのスペル チェック機能を使用できるようにします。|
|**通知設定の変更** (監視モードのみ)|ユーザーがデバイスの通知設定を変更することを許可します。|
|**Spotlight 検索でインターネットから結果を返す** (監視モードのみ)|スポットライト検索でインターネットに接続してさらに多くの検索結果を取得します。|
|**Siri を使用して、ユーザーが生成したインターネットのコンテンツに対してクエリを実行** (監視モードのみ)|Siri が Web サイトにアクセスして質問に回答することを許可します。|

  
###  <a name="store"></a>ストア  
 これらの設定は、iOS デバイスのみに適用されます。  
  
|設定の名前|詳細|  
|------------------|-------------|  
|**アプリケーション ストア**|デバイスからアプリ ストアにアクセスできるようにします。|  
|**アプリケーション ストアにアクセスするパスワードを入力する**|ユーザーは、アプリ ストアにアクセスするためにパスワードを入力する必要があります。|  
|**アプリ内購入**|ユーザーがアプリ内で購入できるようにします。|
|**Apple Configurator と iTunes を使ったアプリのインストールのみ** (監視モードのみ)|デバイスのホーム画面での App Store を有効または無効にします。 無効にした場合でも、ユーザーは iTunes または Apple Configurator ツールを使ってアプリをインストールおよび更新できます。|
|**iBooks ストアへのアクセス** (監視モードのみ)|ユーザーが iBooks ストアを閲覧してブックを購入することを許可します。|
|**アプリの自動ダウンロード** (監視モードのみ)|他のデバイスで購入したアプリのこのデバイスへの自動ダウンロードを許可します。 この設定は、アプリの更新には影響しません。|

  
###  <a name="browser"></a>ブラウザー  
 これらの設定は、iOS デバイスのみに適用されます。  
  
|設定の名前|詳細|  
|------------------|-------------|  
|**既定のブラウザー**|ユーザーは、既定のインターネット ブラウザーを変更できます。|  
|**オートフィル**|ユーザーは、ブラウザーのオートコンプリートの設定を変更できます。|  
|**アクティブ スクリプト**|ブラウザーで Active X のスクリプトなどのスクリプトを実行できます。|  
|**ポップアップ ブロック**|ブラウザーのポップアップ ブロックを有効または無効にします。|  
|**Cookie**|デバイスに Cookie を保存できるようにします。|  
|**不正の警告**|詐欺目的の疑いがある Web サイトの警告を有効または無効にします。|  
  
###  <a name="content-rating"></a>コンテンツの年齢区分  
 これらの設定は、iOS デバイスのみに適用されます。  
  
|設定の名前|詳細|  
|------------------|-------------|  
|**メディア ストアの過激な描写のコンテンツ**|アプリ ストアから成人向けコンテンツにアクセスできるようにするかどうかを指定します。|  
|**年齢区分の地域**|年齢区分による制限を適用する国を指定します。|  
|**映画の年齢区分**|許可する映画コンテンツの最大年齢区分を指定します。|  
|**TV 番組の年齢区分**|許可する TV 番組の最大年齢区分を指定します。|  
|**アプリの年齢区分**|許可するアプリ コンテンツの最大年齢区分を指定します。| 
|**'アダルト' のフラグが付いている iBook ストアからのコンテンツ** (監視モードのみ)|"アダルト" カテゴリのブックをユーザーがダウンロードできるようにします。| 
  
> [!NOTE]  
>  選択できる年齢区分は、選択した **年齢区分の地域** によって異なります。  
  
###  <a name="cloud"></a>クラウド  
 これらの設定は、iOS デバイスのみに適用されます。  
  
|設定の名前|詳細|  
|------------------|-------------|  
|**クラウドのバックアップ**|iCloud のようなクラウド サービスへのバックアップを許可します。|  
|**暗号化バックアップ**|クラウド サービスへのバックアップを暗号化できるようにします。|  
|**ドキュメントの同期**|ドキュメントをクラウド サービスと同期できるようにします。|  
|**写真の同期**|写真をクラウド サービスと同期できるようにします。| 
|**iCloud フォトライブラリ**|**[いいえ]** に設定すると、ユーザーがクラウドに写真やビデオを保存できる iCloud フォトライブラリが使用できなくなります。 これを **[いいえ]** に設定すると、iCloud フォト ライブラリからデバイスに完全にダウンロードされていない写真はすべてデバイスから削除されます。|
|**iCloud の写真共有**|デバイスで iCloud の写真共有を無効にするには、**[いいえ]** に設定します。|
|**ハンドオフして別のデバイスで作業を継続**|ユーザーがある iOS デバイスで開始した作業を別の iOS または Mac OS X デバイスで続行できるようにします。|
|**管理対象アプリから iCloud にデータを同期**|Intune で管理するアプリがユーザーの iCloud アカウントにデータを同期することを許可します。|

  
###  <a name="security"></a>セキュリティ  
 これらの設定は、iOS デバイスのみに適用されます。  
  
|設定の名前|詳細|  
|------------------|-------------|  
|**カメラ**|デバイスのカメラを使用できるようにします。| 
|**新しいエンタープライズ アプリ作成者を信頼**|アプリ ストアからダウンロードされたのではないアプリを信頼するようにユーザーが選択できます。| 
  
###  <a name="roaming"></a>ローミング  
 これらの設定は、iOS デバイスのみに適用されます。  
  
|設定の名前|詳細|  
|------------------|-------------|  
|**音声通話ローミング**|ローミング中の音声通話を許可します。|  
|**ローミング中の自動同期**|ローミング中にデバイスが自動的に同期されるようにします。|  
|**データ ローミング**|データへのアクセス中にネットワーク間のローミングを許可します。|  
  
###  <a name="system-security"></a>システム セキュリティ  
 これらの設定は、iOS デバイスのみに適用されます。  
  
|設定の名前|詳細|  
|------------------|-------------|  
|**信頼されていない TLS 証明書を許可するユーザー**|**[許可]** の場合、ユーザーはこれらの証明書を受け入れることができます。 **[禁止]** の場合は、信頼されていない証明書が自動的に拒否されます。|
|**アクティブ化ロックを許可する (監視モードのみ)**|この設定を使用して、管理する**監視対象** iOS デバイスの iOS アクティベーション ロックを有効にします。 アクティベーション ロックの詳細については、「[System Center Configuration Manager を使用した iOS のアクティベーション ロックの管理](../../mdm/deploy-use/manage-ios-activation-lock.md)」を参照してください。
|**ロック画面のコントロール センター**|デバイスがロックされているときにコントロール センター アプリにアクセスできるかどうかを制御します。|  
|**ロック画面の通知ビュー**|デバイスがロックされているときに通知が表示されるかどうかを制御します。|  
|**ロック画面の今日ビュー**|デバイスがロックされているときに「今日」ビューが表示されるかどうかを制御します。|  
|**アカウント設定の変更** (監視モードのみ)|ユーザーが電子メールの構成などのアカウントの設定を変更することを許可します。|
|**"友達を探す" アプリの設定の変更** (監視モードのみ)|ユーザーが " 友達を探す" アプリの設定を変更することを許可します。|
|**iOS デバイスとペアリングできるデバイスをホスト ペアリングで制御** (監視モードのみ)|ホスト ペアリングを使用して管理者が iOS デバイスとペアリングできるデバイスを制御できるようにします。|
|**すべてのコンテンツと設定を消去** (監視モードのみ)|ユーザーがデバイスのすべてのコンテンツと設定を消去するオプションを使用できるようにします。|
|**デバイスに対する制限の構成** (監視モードのみ)|ユーザーがデバイスにデバイス制限 (保護者による制限) を構成することを許可します。|
|**構成プロファイルと証明書のインストール** (監視モードのみ)|ユーザーが構成プロファイルと証明書をインストールできるようにします。|
|**AirPlay 送信要求のパスワード**|ユーザーが AirPlay を使って他の Apple デバイスにコンテンツをストリーミングするときに、ペアリング パスワードを要求します。|
  
###  <a name="data-protection"></a>データの保護  
 これらの設定は、iOS デバイスのみに適用されます。  
  
|設定の名前|詳細|  
|------------------|-------------|  
|**管理対象のアプリのドキュメントを他の管理されていないアプリで開く**|Configuration Manager のアプリケーション管理ポリシーによって管理されているアプリで使用します。|  
|**管理されていないアプリのドキュメントを他の管理対象のアプリで開く**|Configuration Manager のアプリケーション管理ポリシーによって管理されているアプリで使用します。| 
|**AirDrop を管理対象外として扱う** (監視モードのみ)|管理対象アプリが AirDrop 経由でデータを送信できないようにします 。|
|**AirDrop** (監視モードのみ)|近くにあるデバイスとコンテンツを交換する AirDrop 機能の使用をユーザーに許可します。|
  
###  <a name="compliant-and-noncompliant-apps-ios"></a>準拠アプリと非準拠アプリ (iOS)  
 社内の準拠している (または準拠していない) iOS アプリの一覧を指定できます。 これにより、レポートを使用して、非準拠アプリがインストールされているデバイス、および関連付けられているユーザーを表示できるようになります。  
  
 同一の構成アイテム内で準拠アプリと非準拠アプリの両方を指定することはできません。  
  
#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>準拠アプリまたは非準拠アプリの一覧を指定するには  
  
1.  **[準拠アプリと非準拠アプリ (iOS)]** ページで、次の情報を指定します。  
  
    -   **準拠しないアプリの一覧** - ユーザーがインストールした場合に非準拠として報告されるアプリの一覧を指定するには、このオプションを選びます。  
  
    -   **準拠するアプリの一覧** - ユーザーがインストールできるアプリの一覧を指定するには、このオプションを選びます。 インストールされているその他のすべてのアプリは、非準拠として報告されます。  
  
    -   **追加** - 選んだ一覧にアプリを追加します。 選択した名前と、必要に応じて、アプリの発行者、App Store のアプリへの URL を指定します。  
  
         URL を指定するには、iTunes アプリ ストアで、使用するアプリを検索します。  
  
         アプリのページを開き、URL をクリップボードにコピーします。 準拠アプリおよび非準拠アプリの一覧で URL として使用できるようになります。  
  
         **例:** ストアで **Microsoft Word for iPad** アプリを検索します。 **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8** という URL を使用します。  
  
    -   **編集** - 選んだアプリの名前、発行者、および URL を編集します。  
  
    -   **削除** - 選んだアプリを一覧から削除します。  
  
    -   **インポート** - コンマ区切り値ファイルで指定したアプリの一覧をインポートします。 ファイルの形式、アプリケーション名、発行者、アプリの URL を使用します。  
  
2.  終了したら、 **[次へ]** をクリックします。  
  
 次のレポートのいずれかを使用して、準拠アプリと非準拠アプリを監視できます。  
  
-   **指定されたユーザーの準拠しないアプリケーションとデバイスの一覧** : 指定したポリシーに準拠していないアプリをインストールしたユーザーとデバイスについての情報が表示されます。  
  
-   **非準拠アプリを持つユーザーの概要** - アプリがインストールされ、指定されたポリシーに準拠していないユーザーに関する情報を表示します。  
  
 レポートの使用方法の詳細については、「[System Center Configuration Manager のレポート](../../core/servers/manage/reporting.md)」を参照してください。  
  
###  <a name="compliant-and-noncompliant-apps-mac-os-x"></a>準拠アプリと非準拠アプリ (Mac OS X)  
 社内の準拠している (または準拠していない) Mac OS X アプリの一覧を指定できます。 これにより、レポートを使用して、非準拠アプリがインストールされているデバイス、および関連付けられているユーザーを表示できるようになります。  
  
 同一の構成アイテム内で準拠アプリと非準拠アプリの両方を指定することはできません。  
  
#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>準拠アプリまたは非準拠アプリの一覧を指定するには  
  
1.  **[準拠アプリと非準拠アプリ (Mac OS X)]** ページで、次の情報を指定します。  
  
    -   **準拠しないアプリの一覧** - ユーザーがインストールした場合に非準拠として報告されるアプリの一覧を指定するには、このオプションを選びます。  
  
    -   **準拠するアプリの一覧** - ユーザーがインストールできるアプリの一覧を指定するには、このオプションを選びます。 インストールされているその他のすべてのアプリは、非準拠として報告されます。  
  
    -   **追加** - 選んだ一覧にアプリを追加します。 任意の名前と、必要に応じて、アプリの発行者およびアプリのバンドル ID を指定します。  
  
        > [!TIP]  
        >  アプリのバンドル ID を検索するには、アプリがインストールされている Mac コンピューターで次の手順を使用します。  
        >   
        >  1.  アプリがインストールされているフォルダーを開きます (たとえば、 **/Applications**)。  
        > 2.  *<アプリ名\>***.app** バンドルを選択し、**[パッケージの内容を表示]** を選びます。  
        > 3.  **Info.plist** ファイルを開きます。  
        > 4.  キー **CFBundleIdentifier**に関連付けられた値を確認します。  
        >   
        >  バンドル ID の形式は、 **com.contoso.appname**です。  
  
    -   **編集** - 選んだアプリの名前、発行者、およびバンドル ID を編集します。  
  
    -   **削除** - 選んだアプリを一覧から削除します。  
  
    -   **インポート** - コンマ区切り値ファイルで指定したアプリの一覧をインポートします。 ファイルの形式、アプリ名、発行者、アプリのバンドル ID を使用します。  
  
2.  終了したら、 **[次へ]** をクリックします。  
  
 次のレポートのいずれかを使用して、準拠アプリと非準拠アプリを監視できます。  
  
-   **指定されたユーザーの準拠しないアプリケーションとデバイスの一覧** : 指定したポリシーに準拠していないアプリをインストールしたユーザーとデバイスについての情報が表示されます。  
  
-   **非準拠アプリを持つユーザーの概要** - アプリがインストールされ、指定されたポリシーに準拠していないユーザーに関する情報を表示します。  
  
 レポートの使用方法の詳細については、「[System Center Configuration Manager のレポート](../../core/servers/manage/reporting.md)」を参照してください。  
  
### <a name="ios-and-mac-os-x-custom-profile-settings"></a>iOS および Mac OS X カスタム プロファイルの設定  
 **iOS および Mac OS X カスタム プロファイル** を使用して、 [Apple Configurator ツール](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) で作成した設定を iOS デバイスと Mac OS X デバイスに展開します。 このツールを使用すると、これらのデバイスの動作を制御する多くの設定を作成し、構成プロファイルにエクスポートすることができます。 その後、この構成プロファイルを iOS および Mac OS X カスタム プロファイルにインポートし、組織内のユーザーとデバイスに設定を展開できます。  
  
> [!NOTE]  
>  Apple Configurator ツールからエクスポートした設定に、プロファイルを展開するデバイス上の iOS または Mac OS X のバージョンとの互換性があることを確認します。 互換性のない設定を解決する方法については、 [Apple 開発者](https://developer.apple.com/) Web サイトで「Configuration Profile Reference」および「Mobile Device Management Protocol Reference」を検索してください。  
  
#### <a name="to-create-an-ios-and-mac-os-x-custom-profile"></a>iOS および Mac OS X カスタム プロファイルを作成するには  
  
1.  **構成項目の作成ウィザード** の **[iOS および Mac OS X カスタム プロファイル設定の構成]** ページで、次の情報を指定します。  
  
    -   **カスタム構成プロファイル名 (ユーザーに表示されます)**: ポリシーの名前を指定します。この名前が、デバイスや Configuration Manager レポートに表示されます。  
  
    -   **インポート** - Apple Configurator ツールからエクスポートしたファイルを選びます。  
  
    -   **構成プロファイルの詳細** - インポートしたファイルを表示します。  
  
    -   **対応していない設定を修復する** -  
  
         対応していない構成設定を修復する場合に選択します (サポートされている場合)。  
  
    -   **レポートするコンプライアンス非対応の重要度** - このコンプライアンス ポリシーが非対応として評価される場合に報告する重要度のレベルを指定します。 利用可能な重要度のレベルは、次のとおりです。  
  
        > [!NOTE]  
        >  Mac OS X デバイスがスリープ モードのとき、ポリシーとプロファイルは配信もインベントリもできません。 そのため、Configuration Manager コンソールには、デバイスが次にスリープ モードから復帰するまで一時的に [エラーのあるポリシー設定] という状態が表示される場合があります。  
  
        -   **なし**: このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に非対応重要度を何も報告しません。  
  
        -   **情報**: このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に**情報**というレベルで非対応重要度を報告します。  
  
        -   **警告**: このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に**警告**というレベルで非対応重要度を報告します。  
  
        -   **重大**: このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に**重大**というレベルで非対応重要度を報告します。  
  
        -   **重大 (イベント)**: このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に**重大**というレベルで非対応重要度を報告します。 重要度のレベルは、アプリケーションのイベント ログでも Windows のイベントとしてログが登録されます。  
  
#### <a name="how-to-create-a-configuration-profile-file"></a>構成プロファイル ファイルを作成する方法  
 カスタム ポリシーで使用される構成プロファイル ファイルは、次の 2 つの方法で作成できます。  
  
-   Apple Configurator ツールから、( **.mobileconfig**拡張子の) ファイルをエクスポートします。  
  
-   [Apple 構成プロファイル キー参照](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html)の適切なスキーマを使用して、ファイルを自分で作成します。  
  
###  <a name="kiosk-mode-ios"></a>キオスク モード (iOS)  
 キオスク モードでは、特定の機能のみ実行できるようにデバイスをロックできます。 たとえば、指定した 1 つの管理対象アプリの実行のみをデバイスに許可することや、デバイスのボリューム ボタンを無効にすることができます。 これらの設定は、デバイスのデモ モデルや、POS デバイスなどの 1 つの機能の実行専用のデバイス向けに使用できます。  
  
#### <a name="to-configure-kiosk-mode-for-ios-devices"></a>iOS デバイスのキオスク モードを構成するには  
  
1.  **構成項目の作成ウィザード** の **[iOS デバイスのキオスク モード設定の構成]** ページで、次の情報を指定します。  
  
    -   **アプリの選択** - デバイスがキオスク モードのときに実行が許可されるアプリを選びます。 他のアプリはデバイスでの実行が許可されません。 次の中から選択します。  
  
        -   **[管理対象アプリ]** - [参照] をクリックして管理対象アプリを選択します。  
  
        -   **[ストア アプリ]** - アプリ ストア上のアプリの URL を指定し、 **[アプリ ID の取得]** をクリックして **[アプリ ID]** フィールドを設定します。  
  
         アプリの URL を見つけるには、次の操作を実行します。  
  
        -   検索エンジンを使用して、iTunes App Store で使用するアプリを検索し、アプリのページを開きます。  
  
        -   ページの URL をコピーし、これをキオスク モードで実行するアプリを指定するための URL として使用します。  
  
        -   **例:** **Microsoft Word for iPad**を検索します。 **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8** という URL を使用します。  
  
    -   **タッチ** - デバイスのタッチ スクリーンを有効または無効にします。  
  
    -   **画面の向き** - デバイスを回転するときの画面の向きの変更を有効または無効にします。  
  
    -   **ボリューム ボタン** - デバイスのボリューム ボタンの使用を有効または無効にします。  
  
    -   **着信音スイッチ** - デバイスで着信音 (ミュート) の切り替えを有効または無効にします。  
  
    -   **画面のスリープと復帰のボタン** - デバイスの画面のスリープと復帰のボタンを有効または無効にします。  
  
    -   **自動ロック** - デバイスの自動ロックを有効または無効にします。  
  
    -   **モノ オーディオ** - ユーザー補助の設定 **[モノ オーディオ]** を有効または無効にします。  
  
    -   **ボイス オーバー** - デバイスのディスプレイ上のテキストを音読するユーザー補助の設定 **[ボイス オーバー]** を有効または無効にします。  
  
    -   **ボイス オーバーの調整** - ボイス オーバー機能 (画面に表示されるテキストの読み上げ速度など) の調整を可能にする [ボイス オーバーの調整] を有効または無効にします。  
  
    -   **ズーム** - デバイス ディスプレイでのタッチを使用したズームを可能にするユーザー補助の設定 **[ズーム]** を有効または無効にします。  
  
    -   **ズームの調整** - ズーム機能の調整を可能にする [ズームの調整] を有効または無効にします。  
  
    -   **色の反転** - 視覚障碍を持つユーザーを支援するためにディスプレイの調整するユーザー補助の設定 **[色の反転]** を有効または無効にします。  
  
    -   **色の反転の調整** - 色反転機能の調整を可能にする [色の反転の調整] を有効または無効にします。  
  
    -   **Assistive Touch** - ユーザーが実行しにくいことがある画面の操作をユーザーが実行できるようにするユーザー補助の設定 **[Assistive Touch]** を有効または無効にします。  
  
    -   **Assistive Touch 調整** - Assistive Touch 機能の調整を可能にする [Assistive Touch 調整] を有効または無効にします。  
  
    -   **音声認識の選択** - 選んだテキストを読み上げることができるユーザー補助の設定 **[選択範囲を読み上げ]** を有効または無効にします。  
  
    -   **対応していない設定を修復する** - 対応していない構成設定を修復する場合に選びます (サポートされている場合)。  
  
    -   **レポートするコンプライアンス非対応の重要度** - このコンプライアンス ポリシーが非対応として評価される場合に報告する重要度のレベルを指定します。 重要度レベルは次のとおりです。  
  
        -   **なし**: このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に非対応重要度を何も報告しません。  
  
        -   **情報**: このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に**情報**というレベルで非対応重要度を報告します。  
  
        -   **警告**: このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に**警告**というレベルで非対応重要度を報告します。  
  
        -   **重大**: このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に**重大**というレベルで非対応重要度を報告します。  
  
        -   **重大 (イベント)**: このコンプライアンス規則を満たしていないデバイスは、Configuration Manager レポート用に**重大**というレベルで非対応重要度を報告します。 重要度のレベルは、アプリケーションのイベント ログでも Windows のイベントとしてログが登録されます。  
  
## <a name="see-also"></a>関連項目  
 [System Center Configuration Manager クライアントを使用せずに管理されているデバイスの構成項目](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)
