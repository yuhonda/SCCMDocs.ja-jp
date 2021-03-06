---
title: タスク シーケンスの段階的展開を作成する
titleSuffix: Configuration Manager
description: タスク シーケンスの段階的展開を作成する
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: b634ff68-b909-48d2-9e2c-0933486673c5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2bda41cfd01e5ef90771350e650f68a27c3af6ed
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32348635"
---
# <a name="create-phased-deployments-for-a-task-sequence-with-system-center-configuration-manager"></a>System Center Configuration Manager を使用してタスク シーケンスの段階的展開を作成する

*適用対象: System Center Configuration Manager (Current Branch)*

段階的展開は、複数のコレクションでのタスク シーケンスの調整および順序付けされたロールアウトを自動化します。 既定の 2 段階で段階的展開を作成するか、複数の段階を手動で構成できます。 タスク シーケンスの段階的展開は、PXE またはメディア インストールに対応していません。 

>[!NOTE]
> 段階的展開は、Configuration Manager 1802 で導入されたプレリリース機能です。 <!--1356837-->

## <a name="security-scope-and-log-file-information"></a>セキュリティ スコープとログ ファイル情報

**セキュリティ スコープ**:</br>
段階的展開によって作成された展開は、**[すべて]** セキュリティ スコープを持たないユーザーには表示されません。

**ログ ファイル**: </br>
SMS_PhasedDeployment.log

## <a name="create-a-default-two-phased-deployment-for-a-task-sequence"></a>タスク シーケンスの既定の 2 段階展開を作成する

次の手順を使用して段階的展開を作成します。 

1. **[ソフトウェア ライブラリ]** ワークスペースで **[オペレーティング システム]** を展開して、**[タスク シーケンス]** を選択します。

2. 既存のタスク シーケンスを右クリックして、**[Create Phased Deployment]\(段階的展開の作成\)** を選択します。 

3. **[全般]** タブで、段階的展開の名前と説明 (省略可能) を入力し、**[既定の 2 つの段階の展開を自動的に作成する]** を選びます。 

4. **[最初のコレクション]** フィールドと **[2 番目のコレクション]** フィールドを設定します。 **[次へ]** を選択します。

5. **[設定]** タブで、スケジュール設定ごとに 1 つのオプションを選択し、完了したら **[次へ]** を選択します。 
    - **[最初の段階の成功の基準]。** 
        - **[展開の成功率]** - 段階の成功基準に対して展開を正常に完了したデバイスの割合を指定します。 
    - **[最初の段階が成功した後、配置の第 2 段階を開始するための条件]** (いずれかを選択します):
        - **[この段階は遅延期間 (日数) の後、自動的に開始する]** - 最初の段階が成功した後に第 2 段階を開始するまでに待機する日数を選択します。 
        - **[第 2 段階の展開を手動で開始する]** - 最初の段階が成功した後に自動的に第 2 段階を開始しません。 手動で開始する必要があります。 
    - **[デバイスが対象になったら、ソフトウェアをインストールする]** (いずれかを選択します):
        - **[直ちに]** - デバイスが対象になったらすぐに、デバイスへのインストール期限を設定します。
        - **[期限 (デバイスが対象となった時点からの時間)]** - デバイスが対象となってから一定の日数後にインストールの期限を設定します。 

6. **[フェーズ]** タブで最初の段階をクリックし、**[編集]** をクリックします。  **[ユーザー通知]** や **[Windows Embedded デバイスに対してフィルター処理を書き込む]** などの **[ユーザー エクスペリエンス]** を指定します。 **[適用]** をクリックします。

7. **[配布ポイント]** タブでその段階の **[配布ポイント]** 設定を指定します。**[適用]**、**[OK]** の順にクリックします。        

8. **[フェーズ]** タブで、**[ユーザー エクスペリエンス]** と **[配布ポイント]** の第 2 段階を編集します。 **[適用]**、**[OK]** の順にクリックします。

9. **[概要]** タブで選択内容を確認してから、**[次へ]** をクリックし、ウィザードを続行します。

>[!WARNING]
>段階的展開では、タスク シーケンスの展開の[危険性が高い](/sccm/protect/understand/settings-to-manage-high-risk-deployments.md)かどうかは通知されません。 


## <a name="suspend-and-resume-phases-or-move-to-the-next-phase"></a>段階を一時停止して再開するか、次の段階に移行する
場合によっては、段階的展開を手動で中断する、中断した段階的展開を再開する、または次の段階に移行する必要があります。 

### <a name="move-to-the-next-phase"></a>次の段階に移行する
**[第 2 段階の展開を手動で開始する]** 設定を選択する場合、第 2 段階を開始する必要があります。 次の手順を使用して第 2 段階に移行します。 

1. Configuration Manager コンソールで、**[ソフトウェア ライブラリ]** ワークスペースを選択し、**[オペレーティング システム]** を展開して **[タスク シーケンス]** をクリックします。
2. タスク シーケンスを選択します。
3. コンソールの下部にある **[段階的展開]** タブをクリックします。 
4. 段階的展開を右クリックし、**[Move to next phase]\(次の段階に移行\)** を選択します。
![中断、再開、または次の段階への移行](media/Suspend-phased-deployment.PNG)

### <a name="suspend-or-resume-a-phased-deployment"></a>段階的展開の中断または再開
1. Configuration Manager コンソールで、**[ソフトウェア ライブラリ]** ワークスペースを選択し、**[オペレーティング システム]** を展開して **[タスク シーケンス]** をクリックします。
2. タスク シーケンスを選択し、コンソールの下部にある **[段階的展開]** タブをクリックします。 
3. 段階的展開を選択し、リボンの **[中断]** または **[再開]** をクリックします。

## <a name="next-steps"></a>次のステップ
[カスタム タスク シーケンスの作成](create-a-custom-task-sequence.md) </br>
[オペレーティング システム以外の展開用タスク シーケンスの作成](create-a-task-sequence-for-non-operating-system-deployments.md)。 








