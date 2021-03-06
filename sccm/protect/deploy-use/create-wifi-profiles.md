---
title: Wi-Fi プロファイルの作成方法
titleSuffix: Configuration Manager
description: System Center Configuration Manager の Wi-Fi プロファイルを使用して、ワイヤレス ネットワーク設定を組織内のユーザーに展開する方法について説明します。
ms.date: 12/11/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 321b19b2-a093-4b8f-995f-41f74b886eb5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b665143f40973c20307b99c15f94d773d43b4914
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32350811"
---
# <a name="create-wi-fi-profiles"></a>Wi-Fi プロファイルの作成

*適用対象: System Center Configuration Manager (Current Branch)*


System Center Configuration Manager の Wi-Fi プロファイルを使用して、ワイヤレス ネットワーク設定を組織内のユーザーに展開します。 これらの設定を展開して、ユーザーが Wi-Fi 接続に簡単に接続できるようにします。  

 たとえば、接続するすべての iOS デバイスを有効にする Wi-Fi ネットワークがあります。 ワイヤレス ネットワークへの接続に必要な設定が含まれている Wi-Fi プロファイルを作成します。 その後、階層内の iOS デバイスを持つすべてのユーザーに、プロファイルを展開します。 iOS デバイスのユーザーは、ワイヤレス ネットワークの一覧で会社のネットワークを参照し、このネットワークに簡単に接続できるようになります。  

 Wi-Fi プロファイルを使用して、次のデバイスの種類を構成できます。  

-   Windows 8.1 32 ビットを実行するデバイス  

-   Windows 8.1 64 ビットを実行するデバイス  

-   Windows RT 8.1 を実行するデバイス  

-   Windows 10 デスクトップまたは Windows 10 Mobile を実行するデバイス  

[モバイル デバイスの Wi-Fi プロファイルの作成](../../mdm/deploy-use/create-wifi-profiles.md)に関する記事では、Configuration Manager で Wi-Fi プロファイルを使用して、ワイヤレス ネットワーク設定をモバイル デバイス ユーザーに展開する方法について説明しています。

> [!IMPORTANT]  
>  プロファイルを Android、iOS、Windows Phone、および登録されている Windows 8.1 以降の各デバイスに展開するには、これらのデバイスを Microsoft Intune に登録する必要があります。 デバイスの登録方法については、「[管理するデバイスを Intune に登録する](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)」を参照してください。  

 Wi-Fi プロファイルを作成するときに、さまざまなセキュリティ設定を含めることができます。 たとえば、Configuration Manager の証明書プロファイルを使ってプッシュされている、サーバー評価用の証明書やクライアント認証用の証明書を使えます。 証明書プロファイルの詳細については、「[System Center Configuration Manager の証明書プロファイル](introduction-to-certificate-profiles.md)」を参照してください。  

## <a name="create-a-wi-fi-profile"></a>Wi-Fi プロファイルの作成  

1.  Configuration Manager コンソールで、**[資産とコンプライアンス]** > **[コンプライアンス設定]** >  **[会社のリソースへのアクセス]** > **[Wi-Fi プロファイル]** の順に選択します。  

3.  **[ホーム]** タブの **[作成]** グループで、**[Wi-Fi プロファイルの作成]** を選択します。  

1.  **[全般]** ページで、Wi-Fi プロファイルの一意の名前と説明を入力します。  別の Wi-Fi プロファイルの設定を使用する場合は、**[ファイルから既存の Wi-Fi プロファイル項目をインポートする]** を選びます。  

    > [!IMPORTANT]  
    >  インポートする Wi-Fi プロファイルに Wi-Fi プロファイル用の有効な XML が含まれていることを確認します。 Configuration Manager はプロファイルを検証しません。  

3.  **[レポートするコンプライアンス非対応の重要度]** で、クライアント デバイスの Wi-Fi プロファイルがコンプライアンスに対応していない場合 (プロファイルがインストールできなかった場合など) に報告する重要度レベルを指定します。 次のレベルがあります。  

    -   **なし**: このコンプライアンス規則を満たしていないコンピューターは、Configuration Manager レポート用に非対応重要度を何も報告しません。  

    -   **情報**: このコンプライアンス規則を満たしていないコンピューターは、Configuration Manager レポート用に**情報**というレベルで非対応重要度を報告します。  

    -   **警告**: このコンプライアンス規則を満たしていないコンピューターは、Configuration Manager レポート用に**警告**というレベルで非対応重要度を報告します。  

    -   **重大**: このコンプライアンス規則を満たしていないコンピューターは、Configuration Manager レポート用に**重大**というレベルで非対応重要度を報告します。  

    -   **重大 (イベント)**: このコンプライアンス規則を満たしていないコンピューターは、Configuration Manager レポート用に **重大** というレベルで非対応重要度を報告します。 重要度のレベルは、アプリケーションのイベント ログでも Windows のイベントとしてログが登録されます。  

1.  **[Wi-Fi プロファイル]** ページで、ネットワーク名として表示されるデバイスの名前を指定します。  

    > [!IMPORTANT]  
    >  Configuration Manager は、ネットワーク名内のアポストロフィ ( **'** ) またはコンマ ( **,** ) の使用をサポートしていません。  

2.  大文字と小文字を区別する **[SSID]** を指定します。
3.  以下のものを含む、他の適切な接続オプションを選択します。   **[ネットワークが名前 (SSID) をブロードキャストしていない場合に接続する]** 。SSID が非表示である可能性がある場合  

4.  **[セキュリティの構成]** ページで、ワイヤレス ネットワークで使用するセキュリティ プロトコルを選択します。セキュリティで保護されていない場合は **[認証なし (オープン システム)]** を選択します。
    > [!IMPORTANT]  
    >  オンプレミス モバイル デバイスの Wi-Fi プロファイルを作成している場合は、Configuration Manager の Current Branch は次の Wi-Fi セキュリティ構成のみをサポートします。  
    >   
    >  セキュリティの種類: **[WPA2 Enterprise]** または **[WPA2 Personal]**  
    > 暗号化の種類: **[AES]** または **[TKIP]**  
    > EAP の種類: **[スマート カードまたは他の証明書]** または **[PEAP]**  

    > Android デバイスの場合、セキュリティの種類のうち、**[WPA - パーソナル]** 、 **[WPA2 - パーソナル]**、**[WEP]** はサポートされていません。  

2.  ワイヤレス ネットワークで使用する暗号化方法を選択します。  

3.  ワイヤレス ネットワークで認証に使用する EAP の種類を選択します。  

     Windows Phone デバイスの場合のみ: EAP の種類のうち **[LEAP]** と **[EAP-FAST]** はサポートされていません。  

4.  **[構成]** をクリックして、選択した EAP の種類のプロパティ指定します。 選択した EAP の種類によっては、このオプションを使用できません。  

    > [!IMPORTANT]  
    >  **[構成]** をクリックすると、Windows ダイアログ ボックスが開きます。 そのため、Configuration Manager コンソールを実行しているコンピューターのオペレーティング システムが、選択した EAP の種類の構成をサポートしている必要があります。  
    >   
    >  IOS デバイスでは、認証用として非 EAP メソッドを選択した場合は、選択したメソッドに関係なく、MS-CHAP v2 が接続に使用されます。  

5.  ユーザーがログオンのたびに資格情報を入力しなくても済むようにユーザーの資格情報を保存する場合、 **[ログオンのたびにユーザーの資格情報を記憶する]** を選択します。  

6. **iOS デバイスの場合のみ:**  
 Wi-Fi 接続に必要なすべての証明書に関する情報を構成します。 次の手順に従って、クライアント証明書と、信頼されたサーバー証明書の名前またはルート証明書を構成する必要があります。  

    -   **信頼されたサーバー証明書の名前**: デバイスから接続するサーバーが、サーバー認証証明書を使用してサーバーを識別して通信チャネルを保護する場合は、その証明書のサブジェクト名、またはサブジェクトの別名にある名前を入力します。 通常、この名前はサーバーの完全修飾ドメイン名です。 たとえば、証明書のサブジェクト名に指定されたサーバー証明書の共通名が srv1.contoso.com の場合、「 **srv1.contoso.com**」と入力します。サーバー証明書のサブジェクトの別名が複数ある場合は、各名前をセミコロンで区切って入力します。  

    > [!TIP]  
    >  リモート認証ダイヤルイン ユーザー サービス (RADIUS) サーバー (ネットワーク ポリシー サーバーなど) から認証を受けるために、EAP 認証用に選択したクライアント証明書や iOS デバイス認証用のクライアント証明書を使用する場合は、サブジェクトの別名をユーザー プリンシパル名に設定する必要があります。  

    -   **サーバー評価用のルート証明書の選択**: デバイスから接続するサーバーが、デバイスによって信頼されていないサーバー認証証明書を使用する場合は、そのサーバー証明書のルート証明書を含む証明書プロファイルを選択して、デバイスが信頼する証明書チェーンを作成します。  

    -   **[クライアント認証用のクライアント証明書の選択]**:サーバーまたはネットワーク デバイスで、接続しているデバイスを認証するクライアント証明書が必要な場合は、クライアント認証証明書を含む証明書プロファイルを選択します。  

    > [!NOTE]  
    >  ルート証明書とクライアント証明書を構成して、証明書プロファイルとして展開しておかないと、ルート証明書とクライアント証明書を選択することはできません。 証明書プロファイルの詳細については、「[System Center Configuration Manager の証明書プロファイル](introduction-to-certificate-profiles.md)」を参照してください。  

7.  **[詳細設定]** ページで、認証モード、シングル サインオン、Federal Information Processing Standards 準拠などの Wi-Fi プロファイルの詳細設定を行います。 これらのオプションの詳細については、Windows のドキュメントを参照してください。 ウィザードの **[セキュリティの構成]** ページで選択したオプションによっては、詳細設定できない場合や、使用できる設定が異なる場合があります。  

1.  ワイヤレス ネットワークでプロキシ サーバーを使用する場合は、**[プロキシの設定]** ページで、**[この Wi-Fi プロファイルのプロキシ設定を構成する]** をオンにし、構成情報を指定します。  

2. **[サポートされているプラットフォーム]** ページで、Wi-Fi プロファイルをインストールするオペレーティング システムを選択します。 使用可能なすべてのオペレーティング システムに Wi-Fi プロファイルをインストールするには、**[すべて選択]** をクリックします。  

### <a name="next-steps"></a>次のステップ
 Wi-Fi プロファイルの展開方法については、「[System Center Configuration Manager で Wi-Fi プロファイルを展開する方法](deploy-wifi-vpn-email-cert-profiles.md)」を参照してください。  
