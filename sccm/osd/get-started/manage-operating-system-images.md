---
title: オペレーティング システム イメージを管理する
titleSuffix: Configuration Manager
description: Configuration Manager で、Windows Imaging (WIM) ファイルに格納されているオペレーティング システム イメージを管理するために使用できる方法について説明します。
ms.date: 12/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: fab13949-371c-4a4c-978e-471db1e54966
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3b0931671c05604a0115c14a5e7fc5d9c6767b7c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32350104"
---
# <a name="manage-operating-system-images-with-system-center-configuration-manager"></a>System Center Configuration Manager でのオペレーティング システム イメージの管理

*適用対象: System Center Configuration Manager (Current Branch)*

Configuration Manager のオペレーティング システム イメージは、Windows Imaging (WIM) ファイル形式で格納され、コンピューターのオペレーティング システムを正常にインストールおよび構成するのに必要な参照ファイルおよびフォルダーのコレクションを圧縮したものです。 オペレーティング システムのすべての展開シナリオで、オペレーティング システム イメージを選択する必要があります。   既定のオペレーティング システム イメージを使用するか、構成する参照コンピューターからオペレーティング システム イメージを構築することができます。 参照コンピューターを構築する場合は、オペレーティング システム ファイル、ドライバー、サポート ファイル、ソフトウェア更新プログラム、ツール、その他のソフトウェア アプリケーションをオペレーティング システムに追加してから、それをキャプチャしてイメージ ファイルを作成します。 次に、方法別の情報を示します。  

 **既定のイメージ**  

 既定のオペレーティング システム イメージ (install.wim) は、Windows オペレーティング システムのインストール ファイルに含まれています。 このイメージは、ドライバーの標準セットを含む基本的なオペレーティング システム イメージです。 既定のオペレーティング システム イメージを使用する場合は、タスク シーケンスのステップを使用してオペレーティング システムをインストールしてから、アプリをインストールし、その他の構成を行うことができます。  既定のオペレーティング システム イメージは、<*オペレーティング システムのソース パス>*>\Sources\install.wim 内にあります。  

-   **長所**  

    -   イメージのサイズは、キャプチャしたイメージのサイズよりも小さいです。  

    -   タスク シーケンスのステップを使用したアプリのインストールと構成は、より動的です。 たとえば、タスク シーケンスでインストールするアプリや構成を変更することができ、オペレーティング システムのイメージを再適用する必要はありません。  

-   **短所**  

    -   オペレーティング システムのインストールが完了した後、アプリのインストールとその他の構成が行われるため、オペレーティング システムのインストールに要する時間は長くなることがあります。  

 **キャプチャしたイメージ**  

 カスタマイズしたオペレーティング システム イメージを作成するには、対象のオペレーティング システムを使用して参照コンピューターを構築し、アプリをインストールし、設定などを行います。その後、参照コンピューターからオペレーティング システム イメージをキャプチャして、WIM ファイルを作成します。 参照コンピューターを手動で構築することも、タスク シーケンスを使用して構築ステップの一部またはすべてを自動化することもできます。   
カスタマイズしたオペレーティング システム イメージを作成する手順については、「[Customize operating system images](customize-operating-system-images.md)」 (オペレーティング システム イメージをカスタマイズする) を参照してください。  

-   **長所**  

    -   インストール時間は、既定のイメージを使用する場合より短縮されます。 たとえば、アプリは、キャプチャしたオペレーティング システム イメージとともにプレインストールできるため、後からタスク シーケンス ステップを使用してアプリをインストールする必要はありません。  

-   **短所**  

    -   オペレーティング システムのインストールが完了した後、アプリのインストールとその他の構成が行われるため、オペレーティング システムのインストールに要する時間は長くなることがあります。  


##  <a name="BKMK_AddOSImages"></a> Configuration Manager にオペレーティング システム イメージを追加する  
 オペレーティング システム イメージを使用するには、まずイメージを Configuration Manager サイトに追加する必要があります。 オペレーティング システム イメージをサイトに追加するには、次の手順に従ってください。  

#### <a name="to-add-an-operating-system-image-to-a-site"></a>オペレーティング システム イメージをサイトに追加するには  

1.  Configuration Manager コンソールで、**[ソフトウェア ライブラリ]** をクリックします。  

2.  [ **ソフトウェア ライブラリ** ] ワークスペースで、[ **オペレーティング システム**] を展開してから、[ **オペレーティング システム イメージ**] をクリックします。  

3.  **[ホーム]** タブの **[作成]** グループで **[オペレーティング システム イメージの追加]** をクリックして、オペレーティング システム イメージの追加ウィザードを開始します。  

4.  **[データ ソース]** ページで、オペレーティング システム イメージのネットワーク パスを指定します。 たとえば、**\\\server\path\OS.WIM** を指定します。  

5.  **[全般]** ページで、次の情報を指定してから、 **[次へ]** をクリックします。 この情報は、複数のオペレーティング システム イメージを同じサイトに追加するときに識別する目的で役立ちます。  

    -   **[名前]**:イメージの名前を指定します。 規定では、イメージの名前は WIM ファイルから取得されます。  

    -   **バージョン**:バージョンの名前を指定します。  

    -   **コメント**:イメージの簡単な説明を指定します。  

6.  ウィザードを完了します。  

 これで、オペレーティング システム イメージを配布ポイントに配布できるようになりました。  

##  <a name="BKMK_DistributeBootImages"></a> 配布ポイントにオペレーティング システム イメージを配布する  
 オペレーティング システム イメージは、他のコンテンツを配布するのと同じ方法で配布ポイントに配布されます。 ほとんどの場合、オペレーティング システムを展開する前に、少なくとも 1 つの配布ポイントにオペレーティング システム イメージを配布する必要があります。 オペレーティング システム イメージを配布する手順については、「 [Distribute content](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute)」を参照してください。  

##  <a name="BKMK_OSImagesApplyUpdates"></a> ソフトウェア更新プログラムをオペレーティング システム イメージに適用する  
 使用しているオペレーティング システム イメージのオペレーティング システムに適用できる新しいソフトウェア更新プログラムは、定期的にリリースされます。 イメージにソフトウェア更新プログラムを適用するには、あらかじめソフトウェアの更新のインフラストラクチャを配置し、ソフトウェア更新プログラムを正常に同期し、ソフトウェア更新プログラムをサイト サーバー上のコンテンツ ライブラリにダウンロードしておく必要があります。 詳細については、「[ソフトウェアの更新の展開方法](../../sum/deploy-use/deploy-software-updates.md)」を参照してください。  

 適用できるソフトウェア更新プログラムは、指定したスケジュールでイメージに適用できます。 指定のスケジュールで、Configuration Manager によって、選択したソフトウェア更新プログラムをオペレーティング システム イメージに適用してから、必要に応じて、更新されたイメージを配布ポイントに配布します。 インポート時点で適用されたソフトウェア更新プログラムなど、オペレーティング システム イメージに関する情報はサイト データベースに保管されます。 最初の追加以降、イメージに適用されたソフトウェア更新プログラムもサイト データベースに保管されます。 ソフトウェア更新プログラムをオペレーティング システム イメージに適用するウィザードを開始すると、そのイメージにまだ適用していない適用可能なソフトウェア更新プログラムの一覧が選択対象として取得されます。 Configuration Manager は、サイト サーバー上のコンテンツ ライブラリからソフトウェア更新プログラムをコピーし、オペレーティング システム イメージにソフトウェア更新プログラムを適用します。  

 ソフトウェア更新プログラムをオペレーティング システム イメージに適用するには、次の手順を実行します。  

#### <a name="to-apply-software-updates-to-an-operating-system-image"></a>オペレーティング システム イメージにソフトウェア更新プログラムを適用するには  

1.  Configuration Manager コンソールで、**[ソフトウェア ライブラリ]** をクリックします。  

2.  [ **ソフトウェア ライブラリ** ] ワークスペースで、[ **オペレーティング システム**] を展開してから、[ **オペレーティング システム イメージ**] をクリックします。  

3.  ソフトウェア更新プログラムを適用するオペレーティング システム イメージを選択します。  

4.  [ **ホーム** ] タブの [ **オペレーティング システム イメージ** ] グループで、[ **更新のスケジュール** ] をクリックしてウィザードを開始します。  

5.  [ **更新プログラムの選択** ] ページで、オペレーティング システム イメージに適用するソフトウェア更新プログラムを選択してから、[ **次へ**] をクリックします。  

6.  [ **スケジュールの設定** ] ページで、次の設定を指定してから、[ **次へ**] をクリックします。  

    1.  **スケジュール**: オペレーティング システム イメージにソフトウェア更新プログラムを適用するスケジュールを指定します。  

    2.  **エラー時に続行する**: このオプションを選択すると、エラーが発生した場合でも、イメージにソフトウェア更新プログラムがそのまま適用されます。  

    3.  **イメージを使用して配布ポイントを更新する**: このオプションを選択すると、ソフトウェア更新プログラムが適用された後で、配布ポイントのオペレーティング システム イメージが更新されます。  

7.  [ **概要** ] ページで、情報を確認して [ **次へ**] をクリックします。  

8.  **[完了]** ページで、オペレーティング システム イメージにソフトウェア更新プログラムが正常に適用されたことを確認します。  

##  <a name="BKMK_OSImageMulticast"></a> マルチキャスト展開用のオペレーティング システム イメージを準備する  
 マルチキャスト展開を使用して、複数のコンピューターで同時にオペレーティング システム イメージをダウンロードできるようにします。 各クライアントへ個別の接続を経由してイメージのコピーを送信するのではなく、配布ポイントにより、複数のクライアントへイメージをマルチキャストします。 オペレーティング システムの展開方法として[マルチキャストを使用してネットワーク経由で Windows を展開する](../deploy-use/use-multicast-to-deploy-windows-over-the-network.md)を選択した場合は、マルチキャストをサポートするようにオペレーティング システム イメージ パッケージを構成してから、マルチキャスト対応の配布ポイントにオペレーティング システム イメージを配布する必要があります。 次の手順を使用して、既存のオペレーティング システム イメージ パッケージのマルチキャスト オプションを設定してください。  

#### <a name="to-modify-an-operating-system-image-package-to-use-multicast"></a>マルチキャストが使用できるようにオペレーティング システム イメージ パッケージを変更するには  

1.  Configuration Manager コンソールで、**[ソフトウェア ライブラリ]** をクリックします。  

2.  [ **ソフトウェア ライブラリ** ] ワークスペースで、[ **オペレーティング システム**] を展開してから、[ **オペレーティング システム イメージ**] をクリックします。  

3.  マルチキャスト対応の配布ポイントに配布するオペレーティング システム イメージを選択します。  

4.  **[ホーム]** タブの **[プロパティ]** グループで、 **[プロパティ]** をクリックします。  

5.  **[配布の設定]** タブを選択し、次のオプションを構成します。  

    -   **このパッケージのマルチキャストでの送信を許可する (WinPE のみ)**: オペレーティング システム イメージを同時に展開するには、Configuration Manager にこのオプションを選択する必要があります。  

    -   **マルチキャスト パッケージを暗号化する**: 配布ポイントに送信する前にイメージを暗号化するかどうかを指定します。 このオプションは、パッケージに重要な情報が含まれる場合に使用します。 イメージを暗号化しないと、パッケージのコンテンツはクリア テキストでネットワークに公開され、承認されていないユーザーに読み取られる可能性があります。  

    -   **このパッケージをマルチキャストでのみ送信する**:マルチキャスト セッションの間だけ、配布ポイントがイメージを展開するかどうかを指定します。  

         [ **このパッケージをマルチキャストでのみ送信する**] を選択する場合は、オペレーティング システム イメージの展開オプションとして [ **実行中のタスク シーケンスで必要になったときに、ローカルでコンテンツをダウンロードする** ] も指定する必要があります。 オペレーティング システム イメージの展開オプションは、そのイメージの展開時に指定するか、後で展開のプロパティを編集して指定できます。 展開オプションは、展開オブジェクトの [ **プロパティ** ] ページの [ **配布ポイント** ] タブに表示されます。  

6.  [ **OK**] をクリックします。  
