---
title: Unicode および ASCII のサポート
titleSuffix: Configuration Manager
description: System Center Configuration Manager オブジェクトでの Unicode および ASCII 文字のサポートについて説明します。
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 2bdec799-905f-48bc-aed5-2d92134739e8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 6212a22a8ed2fbce7dda19a0b70b0336812b2827
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32338331"
---
# <a name="unicode-and-ascii-support-in-system-center-configuration-manager"></a>System Center Configuration Manager での Unicode および ASCII のサポート

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager では、Unicode 文字を使用して、ほとんどのオブジェクトを作成します。 ただし、オブジェクトによっては ASCII 文字のみをサポートするものや、その他の制限が適用されるものもあります。  

 以下のセクションで、ASCII 文字セットを使用する必要のあるオブジェクトと、追加制限が適用されるオブジェクトについて説明します。  

-   [ASCII 文字を使用するオブジェクト](#BKMK_ASCIIchar)  

-   [その他の制限事項](#BKMK_OtherCharLimitations)  

-   [ローカライズされない Configuration Manager オブジェクト](#BKMK_LangNonLocalize)  

##  <a name="BKMK_ASCIIchar"></a> ASCII 文字を使用するオブジェクト  
 Configuration Manager では、次のオブジェクトを作成する場合にのみ ASCII 文字セットがサポートされます。  

-   サイト コード  

-   すべてのサイト システム サーバーのコンピューター名  

-   次の Configuration Manager アカウント:  

    > [!NOTE]  
    >  ロシア語で実行されるサイトでは、次のアカウントは ASCII 文字と RUS 文字をサポートします。  

    -   クライアント プッシュ インストール アカウント  

    -   稼働状態の基準の公開アカウント  

    -   稼働状態の基準のクエリ アカウント  

    -   管理ポイント データベース接続アカウント  

    -   ネットワーク アクセス アカウント  

    -   ［パッケージ アクセス アカウント］  

    -   標準センダー アカウント  

    -   サイト システムのインストール アカウント  

    -   ソフトウェアの更新ポイントの接続アカウント  

    -   ソフトウェアの更新ポイントのプロキシ サーバー アカウント  

    > [!NOTE]  
    >  役割に基づいた管理権限を持つアカウントは Unicode をサポートします。  
    >   
    >  レポート サービス ポイント アカウントは、Unicode をサポートしますが、RUS 文字の例外が適用されます。  

-   サイト サーバーとサイト システムの完全修飾ドメイン名 (FQDN)  

-   Configuration Manager のインストール パス  

-   SQL Server インスタンス名  

-   次のサイト システムの役割のパス:  

    -   アプリケーション カタログ Web サービス ポイント  

    -   アプリケーション カタログ Web サイト ポイント  

    -   登録ポイント  

    -   登録プロキシ ポイント  

    -   レポート サービス ポイント  

    -   状態移行ポイント  

-   次のフォルダーのパス:  

    -   クライアントの状態移行データを保管するフォルダー  

    -   Configuration Manager のレポートを格納するフォルダー  

    -   Configuration Manager のバックアップを保管するフォルダー  

    -   サイトのセットアップのインストール ソース ファイルを保管するフォルダー  

    -   セットアップが使用する前提条件のダウンロードを保管するフォルダー  

-   次のオブジェクトのパス:  

    -   IIS の Web サイト  

    -   仮想アプリケーションのインストール パス  

    -   仮想アプリケーション名  

-   AMT と帯域外管理用の次のオブジェクト:  

    -   AMT 搭載コンピューターの FQDN  

    -   AMT 搭載コンピューターのコンピューター名  

    -   ドメイン NetBIOS 名  

    -   ワイヤレス プロファイル名と SSID  

    -   信頼されたルート証明機関名  

    -   証明機関 (CA) の名前とテンプレート名  

    -   IDE リダイレクト イメージ ファイルのファイル名とパス  

    -   AMT データ記憶域のコンテンツ  

-   ブート メディアの .ISO ファイル名  

##  <a name="BKMK_OtherCharLimitations"></a> その他の制限事項  
 サポートされる文字セットと言語バージョンに関するその他の制限事項は以下のとおりです。  

-   Configuration Manager は、サイト サーバー コンピューターのロケールの変更をサポートしません。  

-   エンタープライズ証明機関 (CA) は、2 バイト文字セット (DBCS) を使用するクライアント コンピューター名をサポートしません。 使用可能なクライアント コンピューター名は、PKI の IA5 文字の制限を受けます。 さらに、Configuration Manager では、DBCS を使用する CA 名またはサブネット名値をサポートしていません。  

##  <a name="BKMK_LangNonLocalize"></a> ローカライズされない Configuration Manager オブジェクト  
 Configuration Manager データベースは、保存されるほとんどのオブジェクトに対して Unicode をサポートし、可能な場合、この情報をコンピューターのロケールと一致するオペレーティング システム言語で表示します。 クライアント インターフェイスまたは Configuration Manager コンソールで、情報をコンピューターのオペレーティング システム言語で表示するためには、コンピューターのロケールが、サイトにインストールしているクライアントの言語またはサーバーの言語と一致している必要があります。  

 ただし、一部の Configuration Manager オブジェクトは Unicode をサポートしていないため、それらのオブジェクトは ASCII を使用してデータベースに保存されるか、言語に関する追加の制限事項が発生します。 この情報は常に、ASCII 文字セットを使用して表示されるか、オブジェクトの作成時に使用した言語で表示されます。  
