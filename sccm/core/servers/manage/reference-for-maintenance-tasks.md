---
title: メンテナンス タスクのリファレンス
titleSuffix: Configuration Manager
description: System Center Configuration Manager サイトの各メンテナンス タスクの詳細およびそれらのタスクが既定で有効になるかどうかについて説明します。
ms.date: 3/8/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 68dc6acd-5848-47a4-b4c1-ffa40e47890b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5492382afdb523846fcdd40b68d498730073eb7e
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32342445"
---
# <a name="reference-for-maintenance-tasks-for-system-center-configuration-manager"></a>System Center Configuration Manager のメンテナンス タスクのリファレンス

*適用対象: System Center Configuration Manager (Current Branch)*

このトピックでは、System Center Configuration Manager サイトのメンテナンス タスクを列挙し、それぞれ詳しく説明すると共に、そのタスクが利用できるサイトの種類を明記しています。 それぞれのタスクが既定で有効になっているかどうかも併せて記載しています。 メンテナンス タスクを実行するためにサイトを計画および構成する方法については、「[System Center Configuration Manager のメンテナンス タスク](../../../core/servers/manage/maintenance-tasks.md)」を参照してください。  

**サイト サーバーのバックアップ**: 重要なデータをいつでも回復できるように備えるには、このタスクを使用します。 重要な情報のバックアップを作成しておくことで、サイトや Configuration Manager データベースを復元することができます。 詳細については、「[Backup and recovery for System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md)」 (System Center Configuration Manager のバックアップと回復) をご覧ください。  

-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 無効    
-   セカンダリ サイト: 利用不可  

**インベントリ情報のアプリケーション タイトルの確認**: このタスクは、ソフトウェア インベントリに報告されているソフトウェア タイトルと資産インテリジェンス カタログのソフトウェア タイトル間の整合性を維持するために使用します。 詳細については、「[System Center Configuration Manager の資産インテリジェンスの概要](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md)」を参照してください。  

-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**インストール フラグのクリア**: このタスクは、**[クライアント再探索]** 期間に定期探索レコードを送信しないクライアントのインストール済みフラグを削除する場合に使用します。 インストール済みフラグは、アクティブな Configuration Manager クライアントを持つコンピューターに、自動クライアント プッシュ インストールが行われることを防ぎます。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 無効    
-   セカンダリ サイト: 利用不可  

**期限切れのアプリケーション要求データの削除**: このタスクは、期限切れのアプリケーション要求をデータベースから削除する場合に使用します。 アプリケーション要求の詳細については、「[System Center Configuration Manager でのアプリケーションの作成と展開](/sccm/apps/get-started/create-and-deploy-an-application)」を参照してください。  

-   中央管理サイト: 利用不可
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れのクライアントのダウンロード履歴の削除**: このタスクは、クライアントが使用するソースのダウンロードに関する履歴データを削除する場合に使用します。 ソースのダウンロードに関する情報は、[クライアント データ ソース ダッシュボード](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard)の設定に使用されます。  
-  中央管理サイト – 利用不可
-    **プライマリ サイト** - 有効
-  セカンダリ サイト - 利用不可

**期限切れのクライアント操作を削除**: このタスクは、クライアント操作のすべての期限切れデータをサイト データベースから削除する場合に使用します。 たとえば、これには古いまたは期限切れのクライアント通知のデータ (コンピューターまたはユーザーのポリシーのダウンロード要求など)、および Endpoint Protection のデータ (クライアントが更新された定義をスキャンまたはダウンロードするために管理ユーザーによって実行される要求など) が含まれます。

-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れクライアントのプレゼンス履歴の削除**: このタスクは、指定した時間よりも古い、クライアント通知によって記録されたクライアントのオンライン ステータスに関する履歴情報を削除する場合に使用します。 クライアント通知の詳細については、「[System Center Configuration Manager でクライアントを監視する方法](../../../core/clients/manage/monitor-clients.md)」を参照してください。  

-   **中央管理サイト**: 有効   
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れのクラウド管理ゲートウェイ トラフィック データの削除**: このタスクは、サイト データベースから[クラウド管理ゲートウェイ](/sccm/core/clients/manage/plan-cloud-management-gateway)を通過するトラフィックに関するすべての期限切れデータを削除する場合に使用します。 たとえば、これには要求数、要求の合計バイト数、応答の合計バイト数、失敗した要求数、および最大同時要求数に関するデータが含まれます。  
- **中央管理サイト** - 有効
- **プライマリ サイト** - 有効
- セカンダリ サイト - 利用不可


**期限切れの収集ファイルの削除**: このタスクは、収集するファイルに関する期限切れの情報をデータベースから削除する場合に使用します。 また、このタスクは、選択したサイトのサイト サーバーのフォルダー構造から収集したファイルを削除します。 既定では、収集ファイルのうち、新しい順に 5 ファイルが、サイト サーバーの **Inboxes\sinv.box\FileCol** ディレクトリに格納されます。 詳細については、「[System Center Configuration Manager のソフトウェア インベントリの概要](/sccm/core/clients/manage/inventory/introduction-to-software-inventory)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れのコンピューターの関連付けデータの削除**: このタスクは、オペレーティング システムの展開のコンピューターの関連付けに関する期限切れデータをデータベースから削除する場合に使用します。 この情報は、ユーザー状態を復元する操作で使用されます。 コンピューターの関連付けの詳細については、「[System Center Configuration Manager でのユーザー状態の管理](../../../osd/get-started/manage-user-state.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れの削除検出データの削除**: このタスクは、抽出ビューによって作成されたデータの期限切れデータをデータベースから削除する場合に使用します。 既定では、抽出ビューが無効になります。 有効にするには、Configuration Manager SDK を使用する必要があります。 抽出ビューが有効にされていない場合、このタスクが削除するデータはありません。  

-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れのデバイス ワイプ レコードの削除**: このタスクは、モバイル デバイスのワイプ アクションの期限切れデータをデータベースから削除する場合に使用します。 モバイル デバイスのワイプの詳細については、「[System Center Configuration Manager によるリモート ワイプ、リモート ロック、パスコードのリセットを使用したデータの保護](/sccm/mdm/deploy-use/wipe-lock-reset-devices)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**Exchange Server コネクタで管理される期限切れのデバイスを削除**: このタスクは、Exchange Server コネクタを使用して管理されているモバイル デバイスに関する期限切れデータを削除する場合に使用します。 このデータは、Exchange Server コネクタのプロパティの **[探索]** タブにある **[次の日数以上、非アクティブになっているモバイル デバイスを無視する]** オプションに構成されている間隔に従って削除されます。 詳細については、「[System Center Configuration Manager と Exchange によるモバイル デバイスの管理](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)」を参照してください。  

-   中央管理サイト: 利用不可   
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れの探索データの削除**: このタスクは、期限切れの探索データをデータベースから削除する場合に使用します。 削除されるデータには、定期探索、ネットワーク探索、および Active Directory ドメイン サービスの探索 (システム、ユーザー、およびグループ) などの方法によって作成されたレコードが含まれます。 このタスクは、使用停止とマークされている期限切れデバイスも削除します。 このタスクを 1 つのサイトで実行すると、そのサイトに関連付けられたデータが削除され、それらの変更が他のサイトにレプリケートされます。 探索の詳細については、「 [System Center Configuration Manager 用の探索の実行](../../../core/servers/deploy/configure/run-discovery.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れの配布ポイントの使用状況データの削除**: このタスクは、指定された時間を超えて格納されている配布ポイントの期限切れデータをデータベースから削除する場合に使用します。  

-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**Endpoint Protection の期限切れの正常性状態履歴データを削除**: このタスクは、Endpoint Protection の期限切れの状態情報をデータベースから削除する場合に使用します。 Endpoint Protection 状態情報の詳細については、「[System Center Configuration Manager で Endpoint Protection を監視する方法](../../../protect/deploy-use/monitor-endpoint-protection.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れの登録デバイスの削除**: 1602 用の更新プログラム以降は、このタスクは既定で無効になっています。 このタスクは、指定された期間にサイトにまったく情報を報告しなかったモバイル デバイスに関する期限切れデータをサイト データベースから削除する場合に使用します。

このタスクは、Microsoft Intune (ハイブリッド) によって登録されているデバイス、または Configuration Manager オンプレミス モバイル デバイス管理を使用して登録されているデバイスに適用されます。 Configuration Manager または Intune を使用して登録されたデバイスのオペレーティング システムについては、「[System Center Configuration Manager のクライアントとデバイスのサポートされるオペレーティング システム](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md)」の「[Microsoft Intune で登録されるモバイル デバイス](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md#mobile-devices-enrolled-by-microsoft-intune)」セクションを参照してください。

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 無効    
-   セカンダリ サイト: 利用不可  

**期限切れのインベントリ履歴の削除**: このタスクは、指定された時間を超えて格納されているインベントリ データをデータベースから削除する場合に使用します。 インベントリ履歴の詳細については、「[System Center Configuration Manager でリソース エクスプローラーを使用してハードウェア インベントリを表示する方法](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れのログ データの削除**: このタスクは、トラブルシューティングに使用された期限切れのログ データをデータベースから削除する場合に使用します。 このデータは Configuration Manager コンポーネントの操作には関連していません。  

> [!IMPORTANT]  
> 既定では、このタスクは各サイトで 1 日に 1 回実行されます。 中央管理サイトとプライマリ サイトでは、このタスクによって 30 日よりも古いデータが削除されます。 セカンダリ サイトで SQL Server Express を使用する場合、このタスクが 1 日に 1 回実行されていることを確認し、7 日間非アクティブだったデータを削除します。  

-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 有効    
-   **セカンダリ サイト**: 有効  

**期限切れの通知タスク履歴の削除**: このタスクは、クライアント通知タスクに関する情報が、指定した時間更新されなかったときに、サイト データベースから情報を削除する場合に使用します。 クライアント通知の詳細については、「[System Center Configuration Manager のクライアント展開タスク](../../../core/clients/manage/monitor-clients.md)」を参照してください  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れのレプリケーション概要データの削除**: このタスクは、レプリケーション概要データが、指定した時間更新されなかったときに、サイト データベースから期限切れのデータを削除する場合に使用します。 詳細については、「 [System Center Configuration Manager での階層とレプリケーション インフラストラクチャの監視](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) 」トピックの「 [データベース レプリケーション リンクとレプリケーション ステータスの監視方法](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) 」セクションを参照してください。  

-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 有効    
-   **セカンダリ サイト**: 有効  

**期限切れのパスコード レコードの削除**: このタスクは、Android および Windows Phone デバイスのパスコードのリセットに関する期限切れデータを削除する場合に、階層の最上位サイトで使用します。 パスコードのリセット データは暗号化されますが、デバイスの PIN が含まれます。 既定では、このタスクは有効になり、1 日よりも古いデータを削除します。  

-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れのレプリケーション追跡データの削除**: このタスクは、Configuration Manager サイト間のデータベース レプリケーションに関する期限切れデータをデータベースから削除する場合に使用します。 このメンテナンス タスクの構成を変更すると、その構成が階層内の適用可能な各サイトに適用されます。 詳細については、「 [System Center Configuration Manager での階層とレプリケーション インフラストラクチャの監視](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) 」トピックの「 [データベース レプリケーション リンクとレプリケーション ステータスの監視方法](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) 」セクションを参照してください。  

-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 有効    
-   **セカンダリ サイト**: 有効  

**期限切れのソフトウェア使用状況データの削除**: このタスクは、指定された時間を超えて格納されているソフトウェア使用状況測定の期限切れデータをデータベースから削除する場合に使用します。 詳細については、「[System Center Configuration Manager のソフトウェア使用状況測定](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れのソフトウェア使用状況概要データの削除**: このタスクは、指定された時間を超えて格納されているソフトウェア使用状況測定の期限切れの概要データをデータベースから削除する場合に使用します。 詳細については、「[System Center Configuration Manager のソフトウェア使用状況測定](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れのステータス メッセージの削除**: このタスクは、ステータス フィルター規則に構成されている期限切れのステータス メッセージ データをデータベースから削除する場合に使用します。 詳細については、「[System Center Configuration Manager のアラートとステータス システムの使用](../../../core/servers/manage/use-alerts-and-the-status-system.md)」トピックの「Configuration Manager のステータス システムの監視」セクションを参照してください。  

-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れの脅威データの削除**: このタスクは、指定された時間を超えて格納されている Endpoint Protection の期限切れの脅威データをデータベースから削除する場合に使用します。 Endpoint Protection の詳細については、「[System Center Configuration Manager での Endpoint Protection](../../../protect/deploy-use/endpoint-protection.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れの不明なコンピューターの削除**: このタスクは、不明なコンピューターに関する情報が、指定した時間更新されなかったときに、サイト データベースから情報を削除する場合に使用します。 詳細については、「[System Center Configuration Manager での不明なコンピューターの展開の準備](../../../osd/get-started/prepare-for-unknown-computer-deployments.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れのユーザーとデバイスのアフィニティ データを削除**: このタスクは、期限切れのユーザーとデバイスのアフィニティ データをデータベースから削除する場合に使用します。 詳細については、「[System Center Configuration Manager でのユーザーとデバイスのアフィニティへのユーザーとデバイスの関連付け](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**期限切れの MDM 一括登録パッケージのレコードの削除**: このタスクを利用し、登録証明書の有効期限切れ後、古い一括登録証明書と対応するプロファイルを削除します。 詳細については、「[証明書プロファイルの作成](/sccm/protect/deploy-use/create-certificate-profiles)」をご覧ください。
-   **中央管理サイト**: 有効
-   **プライマリ サイト**: 有効
-   セカンダリ サイト: 利用不可

**非アクティブ クライアントの探索データの削除**: このタスクは、非アクティブ クライアントの探索データをデータベースから削除する場合に使用します。 クライアントが不使用としてフラグ付けされたときに、クライアントのステータスに設定されている構成によって、クライアントは非アクティブとしてマークされます。

このタスクは、Configuration Manager クライアントであるリソースでしか動作しません。 期限切れの探索データ レコードをすべて削除する **[期限切れの探索データの削除]** タスクとは異なります。 このタスクを 1 つのサイトで実行すると、階層内のすべてのサイトのデータベースからそのデータが削除されます。 詳細については、「 [System Center Configuration Manager でクライアント ステータスを構成する方法](../../../core/clients/deploy/configure-client-status.md)」をご覧ください。  

> [!IMPORTANT]  
> 有効にする場合は、**[定期探索]** のスケジュールよりも長い間隔で実行するようにこのタスクを構成します。 これにより、アクティブなクライアントは定期探索レコードを送信できるため、クライアント レコードがアクティブとしてマークされ、このタスクでアクティブなクライアントが削除されることはありません。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 無効    
-   セカンダリ サイト: 利用不可  

**不使用のアラートの削除**: このタスクは、指定された時間を超えて格納されている期限切れのアラートをデータベースから削除する場合に使用します。 詳細については、「 [System Center Configuration Manager のアラートとステータス システムの使用](../../../core/servers/manage/use-alerts-and-the-status-system.md)」を参照してください。  

-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**不使用のクライアントの探索データの削除**: このタスクは、不使用のクライアント レコードをデータベースから削除する場合に使用します。 通常、不使用とマークされたレコードは、同じクライアントの新しいレコードに置き換えられています。 新しいレコードがクライアントの現在のレコードになります。 探索の詳細については、「 [System Center Configuration Manager 用の探索の実行](../../../core/servers/deploy/configure/run-discovery.md)」を参照してください。  

> [!IMPORTANT]  
> 有効にする場合は、[定期探索] のスケジュールよりも長い間隔で実行するようにこのタスクを構成します。 これにより、不使用かどうかを適切に設定する定期探索レコードをクライアントが送信できます。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 無効    
-   セカンダリ サイト: 利用不可  

**不使用のフォレスト探索サイトとサブネットの削除**: このタスクは、過去 30 日間に Active Directory フォレストの探索方法によって発見されなかった Active Directory サイト、サブネット、およびドメインに関するデータを削除する場合に使用します。 これにより、探索データが削除されますが、この探索データから作成された境界には影響しません。 詳細については、「 [System Center Configuration Manager 用の探索の実行](../../../core/servers/deploy/configure/run-discovery.md)」をご覧ください。  

-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**孤立したクライアントの展開状態レコードの削除**: このタスクは、クライアントの展開状態に関する情報を含むテーブルを定期的に消去する場合に使用します。 このタスクにより、古い、または使用停止になったデバイスに関連付けられたレコードが削除されます。  
-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可

**アプリケーションの使用されていないリビジョンの削除**: このタスクは、参照されなくなったアプリケーションのリビジョンを削除する場合に使用します。 詳細については、「[System Center Configuration Manager でアプリケーションを修正して置き換える方法](../../../apps/deploy-use/revise-and-supersede-applications.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**コレクションのメンバーの評価**: コレクション メンバーシップの評価をサイト コンポーネントとして構成します。 サイト コンポーネントについては、「 [System Center Configuration Manager のサイト コンポーネント](../../../core/servers/deploy/configure/site-components.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**キーの監視**: このタスクは、Configuration Manager データベースのプライマリ キーの整合性を監視する場合に使用します。 プライマリ キーは、Microsoft SQL Server データベースのテーブル内で、特定の行を他の行と区別して一意に識別する列 (または複数の列の組み合わせ) です。  

-   **中央管理サイト**: 有効    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**インデックスの再構築**: このタスクは、Configuration Manager データベースのインデックスを再構築する場合に使用します。 インデックスとは、データ検索の速度を上げるためにデータベース テーブルに作成されたデータベース構造のことです。 たとえば、通常、インデックス付きの列の検索は、インデックスが付いていない列の検索よりもかなり速く実行されます。

パフォーマンスを高めるために、Configuration Manager データベースのインデックスは、データベースに保存された流動的なデータと同期を保つために頻繁に更新されます。 このタスクは、50% 以上一意のデータベース列にインデックスを作成し、それ以外の列のインデックスを削除して、データ一意性条件を満たす既存のインデックスをすべて再構築します。  

-   **中央管理サイト**: 無効    
-   **プライマリ サイト**: 無効    
-   **セカンダリ サイト**: 無効  

**インストール済みソフトウェア データの概要**: このタスクは、インストールされているソフトウェアのデータを複数のレコードから単一の汎用レコードに要約する場合に使用します。 データの概要を使用すると、Configuration Manager データベースに格納されるデータ量を圧縮できます。 詳細については、「[System Center Configuration Manager のソフトウェア インベントリの概要](../../clients/manage/inventory\introduction-to-software-inventory.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**ソフトウェア ファイル使用状況データの概要**: このタスクは、ソフトウェア ファイルの使用状況の複数レコードのデータを単一の汎用レコードにまとめる場合に使用します。 データの概要を使用すると、Configuration Manager データベースに格納されるデータ量を圧縮できます。

このタスクを **[ソフトウェア使用状況データの月単位の概要]** タスクと共に使用すると、ソフトウェア使用状況測定データが要約され、Configuration Manager データベース内のディスク領域を節約できます。 詳細については、「[System Center Configuration Manager のソフトウェア使用状況測定](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**ソフトウェア使用状況データの月単位の概要**: このタスクは、月単位のソフトウェアの使用状況の複数レコードのデータを単一の汎用レコードにまとめる場合に使用します。 データの概要を使用すると、Configuration Manager データベースに格納されるデータ量を圧縮できます。

このタスクを **[ソフトウェア ファイル使用状況データの概要]** タスクと共に使用すると、ソフトウェア使用状況測定データが要約され、Configuration Manager データベース内のディスク領域を節約できます。 詳細については、「[System Center Configuration Manager のソフトウェア使用状況測定](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md)」を参照してください。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**アプリケーション対応ターゲット設定の更新**: このタスクは、Configuration Manager がコレクション内のリソースへのポリシーとアプリケーションの展開のマッピングを再計算する場合に使用します。 コレクションにポリシーまたはアプリケーションを展開するときに、Configuration Manager により、展開するオブジェクトとコレクション メンバーの間の初期マッピングが作成されます。

これらのマッピングは、クイック リファレンス用のテーブルに格納されます。 コレクション メンバーシップが変更されたときに、これらの変更を反映するように、これらの格納されたマッピングが更新されます。 ただし、これらのマッピングの同期が取れない可能性があります。たとえば、サイトが通知ファイルを適切に処理できない場合、マッピングに対する変更で、その変更が反映されない可能性があります。 このタスクにより、現在のコレクション メンバーシップに基づいてそのマッピングが更新されます。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  

**アプリケーション カタログ テーブルの更新**: このタスクは、アプリケーション カタログ Web サイト データベースのキャッシュを最新のアプリケーション情報と同期する場合に使用します。 このメンテナンス タスクの構成を変更すると、その構成が階層内のすべてのプライマリ サイトに適用されます。  

-   中央管理サイト: 利用不可    
-   **プライマリ サイト**: 有効    
-   セカンダリ サイト: 利用不可  
