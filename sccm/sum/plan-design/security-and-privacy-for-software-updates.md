---
title: ソフトウェア更新プログラムのセキュリティとプライバシー
titleSuffix: Configuration Manager
description: ソフトウェア更新プログラムのセキュリティのベスト プラクティスおよび Configuration Manager でのプライバシー情報の処理方法について説明します。
author: aczechowski
manager: dougeby
ms.date: 10/06/2016
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 41d6d5d8-ba84-4efb-b105-4d1eed239824
ms.author: aaroncz
ms.openlocfilehash: 3bf98c7b5ae2ee29266203e3496f0b28b1ea134e
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32349186"
---
# <a name="security-and-privacy-for-software-updates-in-system-center-configuration-manager"></a>System Center Configuration Manager のソフトウェア更新プログラムのセキュリティとプライバシー

*適用対象: System Center Configuration Manager (Current Branch)*

このトピックには、System Center Configuration Manager におけるソフトウェア更新プログラムのセキュリティとプライバシーの情報が含まれています。  

##  <a name="BKMK_Security_HardwareInventory"></a> ソフトウェア更新プログラムに関するセキュリティ上のベスト プラクティス  
 クライアントにソフトウェア更新プログラムを展開するときは、次のようなセキュリティのベスト プラクティスに従ってください。  

-   ソフトウェアの更新パッケージに対する既定のアクセス許可を変更しない。  

     既定では、ソフトウェアの更新パッケージは、管理者に **フル コントロール** を許可し、ユーザーに **読み取り** アクセスを付与するように設定されます。 これらのアクセス許可を変更すると、攻撃者によるソフトウェア更新プログラムの追加または削除が可能になる危険性があります。  

-   ソフトウェア更新プログラムのダウンロード先へのアクセスを制御する。  

     ソフトウェア更新プログラムを実際にダウンロード先にダウンロードする管理者と SMS プロバイダー、サイトサーバーのコンピューター アカウントは、ダウンロード先への **[書き込み]** アクセス許可が必要です。 ダウンロード先へのアクセスを制限して、そこにあるソフトウェアの更新のソース ファイルを攻撃者が改ざんするリスクを低減します。  

     さらに、ダウンロード先で UNC 共有を使用する場合は、ネットワークを通じて転送するときにソフトウェア更新のソース ファイルが改ざんされることを防ぐため、IPsec または SMB 署名 を使用して、ネットワーク チャネルをセキュリティ保護してください。  

-   展開時刻の評価に UTC を使用する。  

     UTC ではなくローカル時刻を使用する場合は、ユーザーがコンピューターのタイム ゾーンを変更していると、ソフトウェア更新プログラムのインストールが遅れる可能性があります。  

-   Windows Server Update Services (WSUS). の SSL を有効にし、WSUS をセキュリティ保護するためのベスト プラクティスに従います。  

     Configuration Manager で使用する WSUS のバージョン用のセキュリティのベストプラクティスを確認し、これに従います。  

    > [!IMPORTANT]  
    >  WSUS サーバーで SSL コミュニケーションを有効にするようにソフトウェア更新ポイントを構成する場合は、WSUS サーバーの SSL の仮想ルートを構成する必要があります。  

-   CRL チェックを有効にする  

     既定では、Configuration Manager は、ソフトウェア更新プログラムがコンピューターに展開される前に、更新の署名を検証するための証明書失効リスト (CRL) を確認しません。 証明書が使用されるたびに CRL をチェックすることで、失効済み証明書の使用に対するセキュリティを向上できますが、接続に遅れが発生し、CRL チェックを実行するコンピューターの処理の増加を招くことになります。  

     ソフトウェア更新の CRL チェックを有効化する方法の詳細については、「[System Center Configuration Manager でのソフトウェアの更新の CRL チェックを有効にする方法](../get-started/manage-settings-for-software-updates.md#crl-checking-for-software-updates)」を参照してください。  

-   WSUS がカスタム Web サイトを使用するように構成する。  

     ソフトウェアの更新ポイントに WSUS をインストールする場合、既存の IIS 既定 Web サイトを使用するか、またはカスタム WSUS Web サイトを作成するかを選択できます。 他の Configuration Manager サイト システムまたは他のアプリケーションで使用されているのと同じ Web サイトを共有せずに、WSUS サービスが IIS によって専用の仮想 Web サイトでホストされるようにするには、WSUS のカスタム Web サイトを作成してください。  

     詳細については、「[WSUS がカスタム Web サイトを使用するように構成する](plan-for-software-updates.md#BKMK_CustomWebSite)」を参照してください。  

##  <a name="BKMK_Privacy_HardwareInventory"></a> ソフトウェア更新プログラムに関するプライバシー情報  
 ソフトウェアの更新は、クライアント コンピューターをスキャンして、必要なソフトウェアの更新を判断し、情報をサイト データベースに返送します。 ソフトウェアの更新プロセスの間、Configuration Manager では、コンピューターとログオン アカウントを識別する情報がクライアントとサーバー間で送信されることがあります。  

 Configuration Manager は、ソフトウェアの展開プロセスに関するステータス情報を維持します。 状態情報は、送信時や保管時に暗号化されません。 状態情報は、Configuration Manager データベースに保管され、データベース メンテナンス タスクによって削除されます。 状態情報が Microsoft に送信されることはありません。  

 Configuration Manager のソフトウェアの更新を使用してクライアント コンピューターにソフトウェアの更新をインストールする場合は、その更新に関するソフトウェア ライセンス条項の対象となることがあります。これは、Configuration Manager のソフトウェア ライセンス条項とは別個のものです。 Configuration Manager を使用してソフトウェア更新プログラムをインストールする前に、必ずソフトウェア ライセンス条項を確認して同意する必要があります。  

 Configuration Manager では、既定でソフトウェアの更新が実装されることはありません。また、複数の構成手順を実行しなければ、情報が収集されることはありません。  

 ソフトウェア更新プログラムを構成する前に、プライバシー要件について検討してください。  
