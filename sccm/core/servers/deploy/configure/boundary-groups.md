---
title: 境界グループの構成
titleSuffix: Configuration Manager
description: 境界グループを利用して、境界と呼ばれる関連するネットワークの場所を論理的に整理することにより、クライアントがサイト システムを容易に検索できるようにします。
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 5db2926f-f03e-49c7-b44b-e89b1a5a6779
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 79c6796c116fbe4d182827e24f41ae4d1e5242fe
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32342700"
---
# <a name="configure-boundary-groups-for-system-center-configuration-manager"></a>System Center Configuration Manager の境界グループを構成する


*適用対象: System Center Configuration Manager (Current Branch)*

Configuration Manager の境界グループを利用し、関連するネットワークの場所 ([境界](/sccm/core/servers/deploy/configure/boundaries)) を論理的に編成し、インフラストラクチャの管理を簡単にします。 境界グループを使用するには、事前に境界を境界グループに割り当てておきます。

既定では、Configuration Manager は各サイトで既定のサイト境界グループを作成します。

境界グループを構成するには、境界 (ネットワークの場所) とサイト システムの役割を、配布ポイントのように、境界グループに関連付けます。 この構成は、ネットワーク上のクライアントの近くにある配布ポイントのようにサイト システム サーバーにクライアントを関連付けることに役立ちます。

配布ポイントのように、サイト システム サーバーの可用性を広範囲のネットワークの場所まで広げるには、同じ境界および同じサーバーを複数の境界グループに割り当てます。

クライアントは、次の目的で境界グループを使用します。  

-   サイトの自動割り当て  
-   サービスを提供できるサイト システム サーバーを見つけるため (次を含む):
    - コンテンツの場所の配布ポイント
    -   ソフトウェアの更新ポイント
    - 状態移行ポイント
    - 優先管理ポイント (優先管理ポイントを使用する場合は、境界グループの構成内からではなく、階層に対してこのオプションを有効にする必要があります。 このトピックの「[優先管理ポイントの使用を有効にする](#to-enable-use-of-preferred-management-points)」を参照してください。)

##  <a name="boundary-groups-and-relationships"></a>境界グループとリレーションシップ
階層の境界グループごとに、次を割り当てることができます。

-  1 つまたは複数の境界。 クライアントの**現在**の境界グループは、特定の境界グループに割り当てられた境界として定義されているネットワークの場所となります。 クライアントには複数の現在の境界グループを設定できます。
- 1 つまたは複数のサイト システムの役割。 クライアントは常に、現在の境界グループに関連付けられているサイト システムの役割を使用できます。 追加の構成によっては、追加の境界グループのサイト システムの役割を使用できることがあります。  

作成する境界グループごとに、別の境界グループへの一方向リンクを構成できます。 そのリンクは**リレーションシップ**と呼ばれます。 リンク先の境界グループは**近隣**境界グループと呼ばれます。 境界グループには複数のリレーションシップを設定できます。各リレーションシップに特定の近隣境界グループが与えられます。

クライアントがその現在の境界グループで利用できるサイト システム サーバーを見つけられない場合、そのクライアントが近隣境界グループの検索を開始するタイミングは各リレーションシップの構成により決定します。 この追加グループ検索は**フォールバック**と呼ばれます。

## <a name="fallback"></a>フォールバック
クライアントが現在の境界グループで利用できるサイト システムを見つけられない場合に問題を回避するには、フォールバック動作のために境界グループ間のリレーションシップを定義します。 フォールバックを利用することで、クライアントはその検索範囲を追加の境界グループまで拡大し、利用できるサイト システムを見つけることができます。

リレーションシップは **[リレーションシップ]** タブの境界グループ プロパティで構成されます。リレーションシップを構成するとき、近隣境界グループへのリンクを定義します。 サポートされるサイト システムの役割の種類ごとに、その近隣境界グループへのフォールバックの独立した設定を構成します。 たとえば、ある境界グループに対するリレーションシップを構成するとき、既定の 120 分ではなく、20 分後に配布ポイントのフォールバックが発生するように設定します。 他のさまざまな例については、「[境界グループの使用例](#example-of-using-boundary-groups)」を参照してください。

クライアントがその現在の境界グループで利用できるサイト システムの役割を見つけられない場合、そのクライアントはフォールバック時間 (分単位) を利用します。 近隣境界グループに関連付けられた利用できるサイト システムをクライアントが検索開始するタイミングは、このフォールバック時間により決定されます。  

クライアントは、利用できるサイト システムを見つけられずに近隣境界グループから場所の検索を開始する場合、利用できるサイト システムのプールを増やします。 境界グループおよびそれらのリレーションシップに関する構成では、この利用できるサイト システムのプールに対するクライアントの使用が定義されます。

- 境界グループには複数のリレーションシップを設定できます。 複数のリレーションシップを利用することで、サイト システムの種類ごとにフォールバックを構成し、フォールバック開始までの時間に近隣ごとに別の値を設定できます。    
- クライアントは、現在の境界グループに直接隣接している境界グループにのみフォールバックします。
- クライアントが複数の境界グループのメンバーである場合は、現在の境界グループが、そのクライアントのすべての境界グループの結合として定義されます。 そのクライアントは元のいずれかの境界グループの近隣にフォールバックします。

### <a name="the-default-site-boundary-group"></a>既定のサイト境界グループ
作成する境界グループ以外に、Configuration Manager により作成された既定のサイト境界グループが各サイトに与えられます。 このグループには ***Default-Site-Boundary-Group&lt;sitecode>*** という名前が付きます。 たとえば、サイト ABC のグループの名前は *Default-Site-Boundary-Group&lt;ABC>* になります。

作成する境界グループごとに、Configuration Manager は自動的に、階層の既定の各サイト境界グループに暗黙的リンクを作成します。
-   この暗黙的リンクは、現在の境界グループからサイトの既定の境界グループへの既定のフォールバック オプションです。既定の境界グループには、120 分という既定のフォールバック時間が設定されています。
-   境界グループに関連付けられている境界にないクライアントは、有効なサイト システムの役割を特定するために、それに割り当てられているサイトの既定のサイト境界グループを利用します。

既定のサイト境界グループへのフォールバックを管理するには:
- サイトの既定の境界グループのプロパティを開き、**[既定の動作]** タブの値を変更します。ここで行う変更は、この境界グループの*すべて*の暗黙的リンクに適用されます。 以上の設定は、別の境界グループからこの既定のサイト境界グループの明示的リンクを構成すると無視されます。
- カスタム境界グループのプロパティを開きます。 既定のサイト境界グループへの明示的なリンクの値を変更します。 フォールバックに新しい時間 (分) を設定したり、フォールバックをブロックしたりした場合、その変更はあなたが構成しているリンクにのみ影響を与えます。 明示的リンクの構成は、既定のサイト境界グループの **[既定の動作]** タブの設定より優先されます。


## <a name="site-assignment"></a>サイトの割り当て  
 各境界グループごとに、クライアント用の割り当てられたサイトを構成できます。  

-   サイトの自動割り当てを使用する新しくインストールされたクライアントは、クライアントの現在のネットワークの場所を含む境界グループの割り当て済みサイトに参加します。  
-   サイトに割り当てられると、クライアントがネットワークの場所を変更するときに、クライアントのサイトの割り当てが変更されることはありません。 たとえば、別のサイトが割り当てられた境界グループ内の境界が示されている新しいネットワークの場所にクライアントがローミングしたとしても、クライアントに対して割り当てられたサイトが変更されることはありません。  
-   Active Directory システムの探索で新しいリソースが検出されると、検出されたリソースのネットワーク情報が境界グループ内の境界に対して評価されます。 このプロセスにより、割り当てられたサイトに新しいリソースが関連付けられ、クライアント プッシュ インストール方法で使用できるようになります。  
-   境界が、異なる割り当て済みサイトを持つ複数の境界グループのメンバーである場合は、クライアントによってランダムにいずれかのサイトが選択されます。  
-   境界グループの割り当て済みサイトへの変更は、新しいサイトの割り当て操作にのみ適用されます。 以前にサイトに割り当て済みのクライアントは、境界グループの構成の変更 (またはクライアントのネットワークの場所の変更) に基づくサイトの割り当てを再評価しません。  

クライアントのサイトの割り当ての詳細については、「[System Center Configuration Manager でクライアントをサイトに割り当てる方法](../../../../core/clients/deploy/assign-clients-to-a-site.md)」の「[コンピューターにサイトの自動割り当てを使用する](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_AutomaticAssignment)」をご覧ください。  

## <a name="distribution-points"></a>配布ポイント

クライアントが配布ポイントの場所を要求すると、Configuration Manager によってサイト システムの一覧がクライアントに送信されます。 これらは、クライアントの現在のネットワークの場所が属する各境界グループに関連付けられた適切な種類のサイト システムです。

-   **ソフトウェアの配布時**、クライアントは、配布ポイントまたはその他の有効なコンテンツ ソース (ピア キャッシュに構成されているクライアントなど) から利用できる展開コンテンツの場所を要求します。

-   **オペレーティング システムの展開時**に、クライアントは状態移行情報の送受信用の場所を要求します。  

コンテンツの展開中、クライアントが現在の境界グループ内のソースに対して要求したコンテンツが利用できないものであった場合、クライアントはそのコンテンツに対する要求を続けます。 近隣境界グループまたは既定のサイト境界グループのフォールバック時間に到達するまで、クライアントはその現在の境界グループでさまざまなコンテンツ ソースを試します。 クライアントがコンテンツを見つけていない場合、コンテンツ ソースの検索範囲を拡大し、近隣境界グループを含めます。

コンテンツがオンデマンドで配布されている場合、クライアントからの要求時に配布ポイントでコンテンツが利用できないときには、コンテンツをその配布ポイントに転送するプロセスが開始されます。 クライアントは、フォールバックして近隣境界グループを使用する前に、そのサーバーをコンテンツ ソースとして検索することが可能です。

## <a name="software-update-points"></a>ソフトウェアの更新ポイント
クライアントは境界グループを使用して新しいソフトウェア更新ポイントを見つけます。 クライアントで検索できるサーバーを制御するには、ソフトウェアの更新ポイントをそれぞれ異なる境界グループに追加します。

1702 より前のバージョンから更新すると、各サイトではすべての既存ソフトウェア更新ポイントが既定のサイト境界グループに追加されます。 このサイト更新動作では、利用できるサーバーのプールからソフトウェア更新ポイントを選択するという以前のクライアント動作が続行されます。 この動作は、選択とフォールバックの動作が制御されている異なる境界グループに個々のソフトウェア更新ポイントを追加するまで維持されます。

新しいサイトを設置する場合、既定のサイト境界グループにソフトウェア更新ポイントは追加されません。 クライアントが見つけて利用できるように、ソフトウェア更新ポイントを境界グループに割り当てます。

### <a name="fallback-for-software-update-points"></a>ソフトウェア更新ポイントのフォールバック
ソフトウェア更新ポイントのフォールバックは他のサイト システムの役割と同様に構成されますが、次のような注意点があります。
- **新しいクライアントは境界グループを使用してソフトウェア更新ポイントを選択します。** インストールした新しいクライアントは、構成した境界グループに関連付けられているサーバーからソフトウェア更新ポイントを選択します。 この動作は、クライアントがクライアント フォレストを共有するサーバーのリストからソフトウェアの更新ポイントをランダムに選択する以前の動作に取って代わるものです。

- **クライアントは、フォールバックして新しいソフトウェア更新ポイントを見つけるまで、最後に確認された有効なソフトウェア更新ポイントを引き続き使用します。** ソフトウェア更新ポイントを既に保持しているクライアントでは、到達できなくなるまで、そのソフトウェア更新ポイントが引き続き使用されます。 この動作ではクライアントの現在の境界グループに関連付けられていないソフトウェア更新ポイントも引き続き使用されます。

  そのサーバーがクライアントの現在の境界グループにないときでも、既存のソフトウェア更新ポイントが意図的に引き続き使用されます。 ソフトウェアの更新ポイントが変更されると、クライアントはデータと新しいサーバーを同期します。これによりネットワークの使用率が大きくなります。 すべてのクライアントを新しいサーバーに同時に切り替える場合は、遷移の遅延がネットワークの飽和を回避するのに役立ちます。

- **クライアントはフォールバックを開始する前に、120 分間、最後に確認された有効なソフトウェア更新ポイントへの接続を常に試行します。** 120 分経過し、クライアントが接続を確立していない場合、フォールバックを開始します。 フォールバックを開始すると、クライアントはその現在の境界グループからの全ソフトウェア更新ポイントの一覧を受け取ります。 フォールバック構成に基づき、近隣の境界グループおよびサイト既定の境界グループの付加的ソフトウェア更新ポイントが利用できます。

### <a name="fallback-configurations-for-software-update-points"></a>ソフトウェア更新ポイントのフォールバック構成
#### <a name="beginning-with-version-1706"></a>バージョン 1706 以降   
ソフトウェア更新ポイントの**フォールバック時間 (分単位)** を 120 分未満に構成できます。 ただし、クライアントは引き続き 120 分間、元のソフトウェア更新ポイントへの接続を試行します。 さらに、クライアントは検索範囲を追加のサーバーに拡大します。 境界グループのフォールバック時間は、クライアントが元のサーバーへの接続に最初に失敗したときに開始されます。 クライアントがその検索範囲を拡大すると、サイトはフォールバック時間が 120 分未満に構成された境界グループを提供します。

ソフトウェア更新ポイントのために近隣境界グループにフォールバックする動作をブロックするには、設定を **[フォールバックしない]** に構成します。

2 時間で元のサーバーに到達できないと、クライアントはより短いサイクルを利用し、新しいソフトウェア更新ポイントへの接続を確立します。 これにより、潜在的なソフトウェア更新ポイントが増えてもクライアントは迅速に検索できます。

 -  **フォールバックの例:**  
    クライアントの現在の境界グループにソフトウェア更新ポイントのフォールバックが設定されています。それは境界グループ *A* に対して *10* 分間、境界グループ *B* に対して *130* 分間に構成されています。クライアントが最後に確認された有効なソフトウェア更新ポイントに接続できないとき:
    -   その後 120 分間、元のサーバーのみに接続を試行します。 10 分後、境界グループ A のソフトウェア更新ポイントが利用可能サーバーのプールに追加されます。 ただし、元のサーバーに再接続するための最初の 120 分が経過するまで、クライアントはこの追加サーバーやその他のサーバーへの接続を試行できません。
    -   120 分間、元のソフトウェア更新ポイントの検出を試行した後、クライアントは検索を拡大します。 その時点で、クライアントは、その現在の境界グループおよび 120 分以内に構成された近隣の境界グループにあるソフトウェア更新ポイントの利用可能プールにサーバーを追加します。 このプールには、利用可能サーバーのプールに以前に追加された、境界グループ A のサーバーが含まれます。
    -       さらに 10 分経過すると (クライアントが最後に確認された有効なソフトウェア更新ポイントへの接続を最初に失敗してから合計 130 分後)、クライアントは検索を拡大し、境界グループ B のソフトウェア更新ポイントを追加します。  

#### <a name="prior-to-version-1706"></a>バージョン 1706 以前
バージョン 1706 以前については、ソフトウェア更新ポイントのフォールバック構成では時間 (分単位) を構成できません。 代わりに、フォールバック動作は次のように制限されています。

  - **フォールバック時間 (分単位):** ソフトウェア更新ポイントに対してこのオプションは灰色表示になり、構成できません。 120 分に設定されています。
  -     **フォールバックしない:** この構成を使用すると、ソフトウェア更新ポイントのために近隣境界グループにフォールバックする動作をブロックできます。

ソフトウェア更新ポイントが既に与えられているクライアントは、それに到達できないとき、フォールバックして別のものを見つけます。 フォールバックを利用するとき、クライアントはその現在の境界グループからのソフトウェア更新ポイントの全一覧を受け取ります。 利用できるサーバーが 120 分で見つからなかった場合、近隣境界グループや既定のサイト境界グループにフォールバックします。 両方の境界グループへのフォールバックが同時に実行されます。 近隣グループへのソフトウェアの更新ポイントのフォールバック時間は、120 分に設定されます。 このフォールバック時間を変更することはできません。 120 分は、既定のサイト境界グループへのフォールバックの規定時間でもあります。 クライアントが近隣境界グループと既定のサイト境界グループの両方にフォールバックするとき、クライアントは近隣境界グループからソフトウェア更新ポイントへの接触を試み、それから既定のサイト境界グループのソフトウェア更新ポイントの使用を試みます。

### <a name="manually-switch-to-a-new-software-update-point"></a>新しいソフトウェア更新ポイントに手動で切り替える
フォールバックの利用に加え、*クライアント通知*を利用し、新しいソフトウェア更新ポイントへの切り替えをデバイスに手動で強制できます。

新しいサーバーに切り替えるとき、デバイスはフォールバックを使用してその新しいサーバーを検索します。 境界グループの構成を確認します。 この変更に取り掛かる前に、ソフトウェアの更新ポイントが正しい境界グループにあることを確認してください。

詳細については、「[手動でのクライアントの新しいソフトウェアの更新ポイントへの切り替え](/sccm/sum/plan-design/plan-for-software-updates#manually-switch-clients-to-a-new-software-update-point)」を参照してください。



## <a name="management-points"></a>管理ポイント
<!-- 1324594 -->
バージョン 1802 以降、境界グループ間の管理ポイントのフォールバック関係を構成します。 この動作では、クライアントが使う管理ポイントをいっそうきめ細かく制御できます。 境界グループのプロパティの **[関係]** タブに、管理ポイント用の列があります。 新しいフォールバック境界グループを追加するとき、現在は、管理ポイントのフォールバック時間が常にゼロ (0) になります。 この動作は、サイトの既定の境界グループの **[既定の動作]** でも同じです。

これまでは、セキュリティで保護されたネットワークに保護された管理ポイントがあると、一般的な問題が発生します。 メインの企業ネットワーク上のクライアントは、ファイアウォールを経由してこの保護された管理ポイントと通信できない場合でも、保護された管理ポイントを含むポリシーを受け取ります。 この問題に対処するには、**[フォールバックしない]** オプションを使って、クライアントが通信できる管理ポイントに対してのみフォールバックするようにします。

サイトをバージョン 1802 にアップグレードするとき、Configuration Manager は、インターネットに接続していないすべての管理ポイントを、サイトの既定の境界グループに追加します。 このアップグレード動作により、古いバージョンのクライアントが引き続き管理ポイントと通信できることが保証されます。 この機能を最大限に活用するには、管理ポイントを目的の境界グループに移動します。

管理ポイントの境界グループのフォールバックにより、クライアントのインストール (ccmsetup.exe) 中の動作が変わることはありません。 コマンド ラインで /MP パラメーターを使って初期管理ポイントを指定しないと、新しいクライアントは、利用可能な管理ポイントの完全な一覧を受け取ります。 初期ブートストラップ プロセスでは、クライアントはアクセスできる最初の管理ポイントを使います。 クライアントがサイトに登録した後、クライアントはこの新しい動作で正しく並べ替えられた管理ポイントの一覧を受け取ります。 

この機能を使用するクライアントの場合は、**[階層設定]** の **[クライアントは境界グループで指定された管理ポイントの使用を優先]** を有効にします。 

> [!Note]
> オペレーティング システムの展開プロセスは、境界グループを認識しません。

### <a name="troubleshooting"></a>トラブルシューティング
**LocationServices.log** に新しいエントリが追加されます。 **Locality** 属性は、次のいずれかの状態を示します。
- 0: 不明
- 1: 指定された管理ポイントは、フォールバックに対するサイトの既定の境界グループにのみ存在します
- 2: 指定された管理ポイントは、リモート境界グループまたは近隣の境界グループに存在します。 管理ポイントが近隣の境界グループとサイトの既定の境界グループの両方に存在する場合、ローカリティは 2 です。
- 3: 指定された管理ポイントは、ローカル境界グループまたは現在の境界グループに存在します。 管理ポイントが現在の境界グループと共に、近隣の境界グループまたはサイトの既定の境界グループのどちらかに存在する場合、ローカリティは 3 です。 階層設定で優先管理ポイントの設定を有効にしていない場合は、管理ポイントが存在する境界グループに関係なく、ローカリティは常に 3 です。

クライアントは、最初にローカル管理ポイント (ローカリティ 3)、次にリモート (ローカリティ 2)、最後にフォールバック (ローカリティ 1) を使います。 

クライアントは、10 分間に 5 個のエラーを受け取り、現在の境界グループ内の管理ポイントとの通信に失敗した場合、近隣の境界グループまたはサイトの既定の境界グループの管理ポイントに接続しようとします。 現在の境界グループの管理ポイントが後でオンラインに戻った場合、クライアントは次の更新サイクルでローカル管理ポイントに戻ります。 更新サイクルは、24 時間または Configuration Manager エージェント サービスが再起動するときです。




## <a name="preferred-management-points"></a>優先管理ポイント

 > [!Note]
 > この階層設定の動作 (**[クライアントは境界グループで指定された管理ポイントの使用を優先]**) は、バージョン 1802 以降、変更されています。 この設定を有効にすると、Configuration Manager では割り当てられた管理ポイントの境界グループ機能が使用されます。 詳細については、[管理ポイント](#management-points)に関するセクションをご覧ください。 

 優先管理ポイントを使用すると、クライアントは、その現在のネットワークの場所 (境界) に関連付けられた管理ポイントを特定できます。  

-   クライアントは、割り当て済みサイトからの、優先管理ポイントとして構成されていない管理ポイントを使用する前に、割り当て済みサイトからの優先管理ポイントを使用しようとします。  
-   このオプションを使用するには、**[階層設定]** の **[クライアントは境界グループで指定された管理ポイントの使用を優先]** を有効にします。 次に個々のプライマリ サイトで境界グループを構成します。 その境界グループに関連する境界に関連付ける必要がある管理ポイントを含めます。
-   優先管理ポイントを構成すると、クライアントによって管理ポイントのリストが整理され、そのリストの上部に優先管理ポイントが配置されます。 このリストには、クライアントに割り当てられたサイトからのすべての管理ポイントが含められます。  

> [!NOTE]  
>  クライアントのローミングとは、クライアントがそのネットワークの場所を変更することを意味します。 例として、ノート PC をリモート オフィス内の場所に移動する場合が挙げられます。 クライアントはローミングするとき、クライアントに割り当てられたサイトからのサーバーの使用を試みる前に、クライアントの新しい場所にあるローカル サイトからの管理ポイントまたはプロキシ管理ポイントを使用する場合があります。 割り当てられたサイトからのサーバーを一覧したこのリストには、優先管理ポイントが含まれます。 詳細については、[クライアントがサイト リソースやサービスを検索する方法](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md)に関するページを参照してください。  

## <a name="overlapping-boundaries"></a>重複する境界  
 Configuration Manager は、コンテンツの場所について、重複する境界を持つ構成をサポートします。 クライアント ネットワークの場所が複数の境界グループに属する場合:

-   クライアントがコンテンツを要求すると、コンテンツが格納されているすべての配布ポイントのリストが Configuration Manager によってクライアントに送信されます。  
-   クライアントが状態移行情報の送受信をサーバーに要求すると、クライアントの現在のネットワークの場所を含む境界グループに関連付けられたすべての状態移行ポイントのリストが Configuration Manager によってクライアントに送信されます。  

この動作により、コンテンツまたは状態移行情報の転送元となる最も近いサーバーをクライアントが選択できるようになります。  



## <a name="example-of-using-boundary-groups"></a>境界グループの使用例
次の例では、クライアントは配布ポイントからコンテンツを探します。 この例は、境界グループを利用する他のサイト システムの役割にも適用できます。 ソフトウェア更新ポイントでは近隣グループへのフォールバックの構成がサポートされておらず、常に 120 分という時間が使用されることに留意してください。

境界またはサイト システム サーバーを共有しない次の 3 つの境界グループを作成します。
-   配布ポイント DP_A1 と DP_A2 が関連付けられたグループ BG_A
-   配布ポイント DP_B1 と DP_B2 が関連付けられたグループ BG_B
-   配布ポイント DP_C1 と DP_C2 が関連付けられたグループ BG_C

クライアントのネットワークの場所を境界として、BG_A の境界グループにのみ追加します。 次に、その境界グループと、他の 2 つの境界グループとのリレーションシップを構成します。
-   10 分後に使用する 1 つ目の "*近隣*" グループ (BG_B) に配布ポイントを構成します。 このグループには、配布ポイント DP_B1 と DP_B2 が含まれています。 どちらも、最初のグループの境界の場所に適切に接続されています。
-   20 分後に使用するように 2 つ目の "*近隣*" グループ (BG_C) を構成します。 このグループには、配布ポイント DP_C1 と DP_C2 が含まれています。 どちらも、他の 2 つの境界グループから WAN を経由します。
-   また、サイト サーバー上にある別の配布ポイントをサイトの既定のサイト境界グループに追加します。 このサーバーは、最小限の推奨されるコンテンツ ソースの場所ですが、すべての境界グループの中心的な場所に配置されます。

    境界グループとフォールバック時間の例:

     ![境界グループとフォールバック時間の例](media/BG_Fallback.png)


この構成では:
-   クライアントは "*現在*" の境界グループ (BG_A) 内の配布ポイントからコンテンツの検索を開始します。 クライアントは各配布ポイントを 2 分間検索してから、境界グループ内の次の配布ポイントに切り替えます。 有効なコンテンツ ソースの場所のクライアントのプールには、DP_A1 と DP_A2 が含まれています。
-   クライアントは*現在の* 境界グループを 10 分間検索してコンテンツが見つからなかった場合、BG_B 境界グループから配布ポイントを検索に追加します。 さらに、結合されたサーバーのプール内の配布ポイントからコンテンツの検索を続行します。 このプールには、BG_A と BG_B の両方の境界グループからのサーバーが含められるようになりました。 クライアントは引き続き各配布ポイントを 2 分間検索してから、そのプール内の次のサーバーに切り替えます。 有効なコンテンツ ソースの場所のクライアントのプールには、DP_A1、DP_A2、DP_B1、DP_B2 が含まれています。
-   さらに 10 分 (合計 20 分) 経っても、クライアントがコンテンツがある配付ポイントをまだ見つけられない場合は、そのプールを拡大して、2 番目の "*近隣*" グループ (境界グループ BG_C) からの利用可能なサーバーを含めます。 クライアントは、6 つの配布ポイント (DP_A1、DP_A2、DP_B2、DP_B2、DP_C1、DP_C2) を検索するようになりました。 コンテンツが見つかるまで、2 分ごとに新しい配布ポイントに切り替えていきます。
-   合計で 120 分経ってもクライアントがコンテンツを見つけられない場合は、フォールバックして*既定サイトの境界グループ*を継続的な検索の一部として含めます。 これでプールには構成した 3 つの境界グループからのすべての配布ポイントが含まれ、最後の配布ポイントがサイト サーバー上に配置されました。 クライアントはコンテンツが見つかるまで 2 分ごとに配布ポイントを切り替えてコンテンツの検索を続けます。

さまざまな近隣グループをそれぞれ異なる時刻に利用できるように構成することにより、特定の配布ポイントをコンテンツ ソースの場所として追加するタイミングを制御します。 クライアントは、安全対策として既定のサイトの境界グループへのフォールバックを使用し、他のいずれの場所からもコンテンツが利用できないようにします。





<!--
### Update existing boundary groups to the new model
When you update to version prior to 1610, the following configurations are automatically made. This behavior ensures your current fallback behavior remains available until you configure new boundary groups and relationships.

-   Each primary site creates a default site boundary group named ***Default-Site-Boundary-Group&lt;sitecode>***.
  - The primary site adds to the *Default-Site-Boundary-Group&lt;sitecode>* boundary group any state migration points and distribution points configured to **Allow fallback source location for content**.
  - The site adds software update points to the *Default-Site-Boundary-Group&lt;sitecode>* boundary group.
-   The site makes a copy of each existing boundary group that includes a site server configured with a slow connection. The name of the new group is ***&lt;original boundary group name>-&lt;original boundary group ID>***:  
    -   Site systems that have a fast connection are left in the original boundary group.
    -   A copy of site systems (distribution points, management points) that have a slow connection are added to the copy of the boundary group. The original site systems configured as slow remain in their original boundary groups for backward compatibility, but are not used from those boundary groups.
    - This boundary group copy does not have boundaries associated with it. However, A fallback link is created between the original group and the new boundary group copy that has the fallback time set to zero.  


- **Specific to secondary sites:**
  - If a secondary site has at least one state migration point or distribution point enabled to **Allow fallback source location for content**, Configuration Manager creates a boundary group named ***Secondary-Site-Neighbor--Tmp&lt;Sitecode>***. 
  - All distribution points enabled to **Allow fallback source location for content** and state migration points are added to this secondary site boundary group.
  - A fallback link is created between the original boundary group and the newly created neighbor boundary group. The fallback time is set to zero.


 The following table identifies the new fallback behavior you can expect from the combination the original deployment settings and distribution point configurations:

Original deployment configuration for “Do not run program” in slow network  |Original distribution point configuration for “Allow client to use a fallback source location for content”  |New fallback behavior  
---------|---------|---------
Selected     |  Selected    |  **No fallback** - Only use the distribution points in current boundary group       
Selected     |  Not selected|  **No fallback** - Only use the distribution points in current boundary group       
Not selected |  Not selected|  **Fallback to neighbor** - Use the distribution points in current boundary group, and then add the distribution points from the neighbor boundary group. Unless an explicit link to the default site boundary group is configured, clients do not fallback to that group.    
Not selected | Selected     |   **Normal fallback** - Use distribution points in current boundary group, then servers from the neighbor and site default boundary groups

 All other deployment configurations result in **Normal fallback**.  
-->



## <a name="changes-from-prior-versions"></a>以前のバージョンからの変更
Configuration Manager Current Branch での境界グループに対する主な変更およびクライアントのコンテンツ検索方法に対する主な変更を次に示します。 これらの変更と概念の多くが連動しています。


-   高速または低速の構成の削除: 個々の配布ポイントに高速または低速を設定する必要がなくなりました。 代わりに、境界グループに関連付けられている各サイト システムが同じように処理されます。 この変更により、境界グループ プロパティの **[参照]** タブで高速または低速の構成がサポートされなくなりました。
- 各サイトに新しい既定の境界グループ: 各プライマリ サイトに ***Default-Site-Boundary-Group&lt;sitecode>*** という名前の新しい既定の境界グループが追加されました。 クライアントが境界グループに割り当てられているネットワークの場所にいない場合、そのクライアントは、割り当てられたサイトの既定のグループに関連付けられているサイト システムを使用します。 フォールバックするコンテンツの場所の概念に代わるものとして、この境界グループを使用することを計画してください。   
 -  **[代替のコンテンツ ソースの場所の使用を許可する]** の削除: フォールバックに使用する配布ポイントを明示的に構成する必要がなくなりました。 この設定を構成するオプションは、コンソールから削除されています。

    さらに、アプリケーションの展開の種類で **[代替のコンテンツ ソースの場所の使用をクライアントに許可する]** の設定をオンにした場合の結果が変更されています。 展開の種類でこの設定をオンにすると、クライアントがコンテンツ ソースの場所として既定のサイトの境界グループを使用できるようになりました。

 -  境界グループのリレーションシップ: 各境界グループを 1 つ以上の別の境界グループにリンクできます。 これらのリンクは、**[リレーションシップ]** という名前の新しい境界グループ プロパティ タブに構成されるリレーションシップを形成します。
    -   クライアントに直接関連付けられている各境界グループは、**現在の**境界グループと呼ばれます。  
    -   クライアントの "*現在の*" 境界グループと別のグループとの関連付けによりクライアントが使用できる境界グループはすべて、**近隣**境界グループと呼ばれます。
    -  **[リレーションシップ]** タブで、"*近隣*" 境界グループとして使用する境界グループを追加します。 また、フォールバックに分単位の時間を構成します。 また、クライアントが "*現在の*" グループで配布ポイントからコンテンツを検索できない場合、この時間はクライアントが "*近隣*" 境界グループからコンテンツの場所の検索を開始する時間となります。

        境界グループの構成を追加または変更する場合に、構成している現在のグループから特定の境界グループへのフォールバックをブロックするオプションがあります。

    新しい構成を使用するには、境界グループ間の明示的な関連付け (リンク) を定義します。 その関連付けられているグループ内のすべての配布ポイントを同じ時間 (分単位) で構成します。 クライアントが "*現在の*" 境界グループからのコンテンツ ソースの検索に失敗した場合、設定する時間によって、近隣境界グループからコンテンツ ソースの検索を開始できる時間が決まります。

    明示的に設定した境界グループに加え、各境界グループには既定のサイト境界グループへの暗黙的なリンクもあります。 このリンクは 120 分後にアクティブになります。 既定のサイトの境界グループは、近隣境界グループになります。 この動作により、クライアントは、その境界グループに関連付けられた配布ポイントをコンテンツ ソースの場所として使用することができます。

    これは、以前はコンテンツのフォールバックと呼ばれていた動作に取って代わるものです。 この 120 分の既定の動作は、既定のサイトの境界グループを "*現在*" のグループに明示的に関連付けることにより上書きできます。 特定の時間を分単位で設定するか、フォールバックを完全にブロックすることで、使用できなくなります。


-   クライアントは各配布ポイントからのコンテンツ取得を最大 2 分間試みる: クライアントは、コンテンツ ソースの場所を検索する際に、各配布ポイントへのアクセスを 2 分間試行してから別の配布ポイントを試します。 この動作は、クライアントが配布ポイントへの接続を最大 2 時間試行していた以前のバージョンからの変更点です。

    - クライアントは、その "*現在の*" 境界グループ (複数可) 内の利用可能なサーバーのプールから最初の配布ポイントをランダムに選択します。

    - 2 分後に、クライアントがコンテンツを見つけられない場合は、新しい配布ポイントに切り替えて、そのサーバーからコンテンツを取得しようとします。 このプロセスは、クライアントがコンテンツを見つけるか、そのプール内の最後のサーバーに到達するまで 2 分ごとに繰り返されます。

    - クライアントが "*近隣*" 境界グループへのフォールバック期間に達するまでに、"*現在の*" プールから有効なコンテンツ ソースの場所を見つけられない場合、クライアントはその "*近隣*" グループからの配布ポイントを現在のリストの末尾に追加します。 次にクライアントは、両方の境界グループからの配布ポイントが含まれている拡張されたソース場所グループを検索します。

        > [!TIP]  
        > 現在の境界グループから既定のサイトの境界グループに明示的なリンクを作成し、近隣境界グループへのリンクのフォールバック時間よりも短いフォールバック時間を定義すると、クライアントは、近隣グループを含める前の既定のサイトの境界グループからのソースの場所の検索を開始します。

    - クライアントがプール内の最後のサーバーからのコンテンツの取得に失敗した場合、もう一度プロセスを開始します。


## <a name="procedures-for-boundary-groups"></a>境界グループの手順

### <a name="to-create-a-boundary-group"></a>境界グループを作成するには  
1.  Configuration Manager コンソールで、**[管理]** > **[階層の構成]** >  **[境界グループ]** をクリックします。  

2.  **[ホーム]** タブの **[作成]** グループで、 **[境界グループの作成]** をクリックします。  

3.  **[境界グループの作成]** ダイアログ ボックスで、**[全般]** タブを選択し、この境界グループの **[名前]** を指定します。  

4.  **[OK]** をクリックして新しい境界グループを保存します。  


### <a name="to-configure-a-boundary-group"></a>境界グループを構成するには  
 1.  Configuration Manager コンソールで、**[管理]** > **[階層の構成]** >  **[境界グループ]** をクリックします。  

 2.  変更する境界グループを選択します。  

 3.  **[ホーム]** タブの **[プロパティ]** グループで、 **[プロパティ]** をクリックします。  

 4.  境界グループの **[プロパティ]** ダイアログ ボックスで、 **[全般]** タブを選択してこの境界グループのメンバーである境界を変更します。  

     -   境界を追加するには、 **[追加]** をクリックし、1 つまたは複数の境界のチェック ボックスを選択して、 **[OK]** をクリックします。  

     -   境界を削除するには、境界を選択して **[削除]** をクリックします。  

 5.  **[参照]** タブを選択し、サイトの割り当てと、関連付けられたサイト システム サーバーの構成を変更します。  

     -   この境界グループをサイト割り当て用にクライアントが使用できるようにするには、**[サイト割り当てにこの境界グループを使用する]** を選択します。 次に、**[割り当てられたサイト]** のドロップダウン ボックスからサイトを選択します。  

     -   この境界グループに関連付けられている使用可能なサイト システム サーバーを構成するには:  

     1.  **[追加]** をクリックし、1 つまたは複数のサーバーのチェック ボックスをオンにします。 サーバーは、この境界グループの関連付けられたサイト システム サーバーとして追加されます。 サーバーにインストールされたサイト システムの役割をサポートしているサーバーのみを利用できます。  

         > [!NOTE]  
         >  階層内のすべてのサイトから、利用可能なサイト システムの任意の組み合わせを選択できます。 選択したサイト システムは **[サイト システム]** タブで、この境界グループのメンバーの各境界のプロパティに一覧表示されます。  

     2.  サーバーを境界グループから削除するには、サーバーを選択して **[削除]** をクリックします。  

         > [!NOTE]  
         >  この境界グループが関連するサイト システムに使用されないようにするには、関連付けられたサイト システム サーバーとして表示されているすべてのサーバーを削除します。  

 6.  フォールバック動作を構成するには、**[関係]** タブを選択してください。  

     - **[追加]** をクリックし、構成する境界グループを選択します。

     - 配布ポイントのフォールバック時間を設定します。 この時間が経過すると、関係を構成する境界グループのクライアントは、追加する境界グループの配布ポイントからコンテンツを検索できるようになります。

     - 既定で構成されている "*既定のサイト境界グループ*" を含め、特定の境界グループへのフォールバックを回避するには、境界グループを選択し、**[フォールバックしない]** をオンにします。   

 7.  **[OK]** をクリックして境界グループのプロパティを閉じ、構成を保存します。  

#### <a name="to-associate-a-site-system-server-with-a-boundary-group"></a>サイト システム サーバーを境界グループに関連付けるには  
 1.  Configuration Manager コンソールで、**[管理]** > **[階層の構成]** >  **[境界グループ]** をクリックします。  

 2.  変更する境界グループを選択します。  

 3.  **[ホーム]** タブの **[プロパティ]** グループで、 **[プロパティ]** をクリックします。  

 4.  境界グループの **[プロパティ]** ダイアログ ボックスで、 **[参照]** タブを選択します。  

 5.  **[サイト システム サーバーを選択する]** で **[追加]** をクリックします。 この境界グループに関連付けるサイト システムを選択し、**[OK]** をクリックします。  

 6.  **[OK]** をクリックしてダイアログ ボックスを閉じ、境界グループの構成を保存します。  


#### <a name="to-configure-a-fallback-site-for-automatic-site-assignment"></a>サイトの自動割り当てのフォールバック サイトを構成するには  

  1.  Configuration Manager コンソールで、**[管理]** > **[サイトの構成]** >  **[サイト]** の順にクリックします。  

  2.  **[ホーム]** タブの **[サイト]** グループで、 **[階層設定]** をクリックします。  

  3.  **[全般]** タブで、 **[フォールバック サイトを使用する]** のチェック ボックスをオンにして、 **[フォールバック サイト]** のドロップダウン リストからサイトを選択します。  

  4.  **[OK]** をクリックして構成を保存します。  

#### <a name="to-enable-use-of-preferred-management-points"></a>優先管理ポイントの使用を有効にする  

 1.  Configuration Manager コンソールで、**[管理]** > **[サイトの構成]** > **[サイト]** の順にクリックし、**[ホーム]** タブの **[階層設定]** をクリックします。  

 2.  [階層設定] の **[全般]** タブで、 **[クライアントは境界グループで指定された管理ポイントの使用を優先]** を選択します。  

 3.  **[OK]** をクリックしてダイアログ ボックスを閉じ、構成を保存します。  
