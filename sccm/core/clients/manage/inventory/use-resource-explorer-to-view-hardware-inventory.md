---
title: リソース エクスプローラーを使用してハードウェア インベントリを表示する
titleSuffix: Configuration Manager
description: System Center Configuration Manager でリソース エクスプローラーを使用してハードウェア インベントリを表示します。
ms.date: 01/03/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 375912f5-436d-4315-bdbe-d77afee6c9f3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: be2c8c3dbfef5ea0f35e338b14439c65150310be
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32332211"
---
# <a name="how-to-use-resource-explorer-to-view-hardware-inventory-in-system-center-configuration-manager"></a>System Center Configuration Manager でリソース エクスプローラーを使用してハードウェア インベントリを表示する方法

*適用対象: System Center Configuration Manager (Current Branch)*

System Center Configuration Manager のリソース エクスプローラーを使用して、階層内のクライアントから収集されたハードウェア インベントリに関する情報を表示します。  

> [!NOTE]  
>  リソース エクスプローラーでは、接続するクライアントでハードウェア インベントリ サイクルが実行されるまで、インベントリ データは表示されません。  

 リソース エクスプローラーには、ハードウェア インベントリに関する次のセクションが含まれます。  

-   **[ハードウェア]** - 指定したクライアント デバイスから収集された、最新のハードウェア インベントリが含まれます。  **[ワークステーションのステータス]** には、デバイスがハードウェア インベントリを最後に実行した日付と時刻が表示されます。  

-   **[ハードウェア履歴]** – 前回ハードウェア インベントリが実行されてから変更されたインベントリ項目の履歴が含まれます。 各項目には、**[現在]** ノードと、1 つ以上の *<日付\>* ノードが含まれます。 現在のノードの情報と、履歴ノードの 1 つを比較して、変更された項目を見つけることができます。  

    > [!NOTE]  
    >  Configuration Manager では、**[期限切れのインベントリ履歴の削除]** サイト メンテナンス タスクで、サイトに対して指定されている日数だけ、インベントリの履歴が保持されます。  

> [!NOTE]  
>  Linux および UNIX を実行しているクライアントからハードウェア インベントリを表示する方法については、「 [System Center Configuration Manager で Linux および UNIX サーバーのクライアントを監視する方法](../../../../core/clients/manage/monitor-clients-for-linux-and-unix-servers.md)」を参照してください。  

### <a name="how-to-run-resource-explorer-from-the-configuration-manager-console"></a>Configuration Manager コンソールからリソース エクスプローラーを実行する方法  

1.  Configuration Manager コンソールで、**[資産とコンプライアンス]** > **[デバイス]** を選択するか、デバイスを表示する任意のコレクションを開きます。  

3.  表示するインベントリが含まれているコンピューターをクリックしたら、**[ホーム]** タブの **[デバイス]** グループで **[開始]** >  **[リソース エクスプローラー]** の順に選択します。   

4.  **[リソース エクスプローラー]** ウィンドウの右ウィンドウの項目を右クリックし、**[プロパティ]** をクリックして、*[<項目名\>*** のプロパティ*]* ダイアログ ボックスを開くことができます。このダイアログ ボックスには、収集されたインベントリ情報を、より読みやすい形式で表示できます。  

