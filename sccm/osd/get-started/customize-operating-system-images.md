---
title: "オペレーティング システム イメージをカスタマイズする | Configuration Manager"
description: "キャプチャとビルドのタスク シーケンスもしくは手動構成、またはこの両方の組み合わせを使用して、オペレーティング システム イメージをカスタマイズします。"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 95033a9b-ff13-4b70-b1de-bcb25bcb6024
caps.latest.revision: 12
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: e7e0ecf394297799c2a3d0c14e719182b403e1e8


---
# <a name="customize-operating-system-images-with-system-center-configuration-manager"></a>System Center Configuration Manager でのオペレーティング システム イメージのカスタマイズ

*適用対象: System Center Configuration Manager (Current Branch)*

Configuration Manager のオペレーティング システム イメージは WIM 形式のファイルで、コンピューターにオペレーティング システムを正常にインストールして構成するのに必要な、参照ファイルとフォルダーのコレクションを圧縮したものです。 カスタムのオペレーティング システム イメージは、参照コンピューターから構築およびキャプチャし、オペレーティング システム ファイル、サポート ファイル、ソフトウェア更新プログラム、ツール、その他のソフトウェア アプリなど、必要なものをすべて含めて構成します。 参照コンピューターを手動で構成する範囲は、ユーザーが決められます。 参照コンピューターの構成は、構築およびキャプチャのタスク シーケンスを使用して完全に自動化することができます。また、参照コンピューターの特定の要素を手動で構成してから、タスク シーケンスを使用して残りを自動化したり、タスク シーケンスを使用せずに参照コンピューターを手動で構成したりもできます。 次のセクションを使用して、オペレーティング システムをカスタマイズします。

##  <a name="a-namebkmkpreparereferencecomputera-prepare-for-the-reference-computer"></a><a name="BKMK_PrepareReferenceComputer"></a> 参照コンピューターの準備  
 参照コンピューターからオペレーティング システム イメージのキャプチャを行う前に、次の点をご検討ください。  

###  <a name="a-namebkmkrefcomputerdecidea-decide-between-an-automated-or-manual-configuration"></a><a name="BKMK_RefComputerDecide"></a> 自動または手動の構成の決定  
 次に、参照コンピューターの自動構成と手動構成の長所と短所を示します。  

#### <a name="automated-configuration"></a>自動構成  
 **長所**  

-   構成を完全に無人で実行でき、管理者またはユーザーが同席する必要がありません。  

-   タスク シーケンスを再利用し、安心して追加の参照コンピューターの構成を繰り返すことができます。  

-   タスク シーケンス全体を再度作成せずに、タスク シーケンスを変更して参照コンピューターの違いに対応できます。  

 **短所**  

-   最初にタスク シーケンスを構築するときは、作成とテストに時間がかかります。  

-   参照コンピューターの要件が大きく変化した場合、タスク シーケンスを再構築および再テストする時間が必要です。  

#### <a name="manual-configuration"></a>手動構成  
 **長所**  

-   タスク シーケンスを作成する必要がなく、タスク シーケンスのテストやトラブルシューティングの時間も不要です。  

-   CD から直接インストールでき、すべてのソフトウェア パッケージ (Windows 自体を含む) を Configuration Manager パッケージに入れる必要がありません。  

 **短所**  

-   参照コンピューターの構成精度が、コンピューターを構成している管理者またはユーザーにより変化します。  

-   参照コンピューターが正しく構成されたことを検証し、テストする必要があります。  

-   構成方法を再利用することはできません。  

-   プロセス全体にアクティブに関わる人が必要です。  

###  <a name="a-namebkmkrefcomputerconsiderationsa-considerations-for-the-reference-computer"></a><a name="BKMK_RefComputerConsiderations"></a> 参照コンピューターの考慮事項  
 次に、参照コンピューターを構成するときに考慮する基本項目の一覧を示します。  

-   **展開するオペレーティング システム**  

     参照コンピューターには、対象となるコンピューターに展開するオペレーティング システムをインストールする必要があります。 展開できるオペレーティング システムの詳細については、「[Infrastructure requirements for operating system deployment](../plan-design/infrastructure-requirements-for-operating-system-deployment.md)」 (オペレーティング システムの展開のインフラストラクチャの要件) をご覧ください。  

-   **適切なサービス パック**  

     参照コンピューターには、対象となるコンピューターに展開するオペレーティング システムをインストールする必要があります。  

-   **適切なソフトウェア更新プログラム**  

     参照コンピューターからキャプチャするオペレーティング システム イメージに含めるソフトウェア アプリケーションをすべてインストールします。 キャプチャされたオペレーティング システム イメージを対象となるコンピューターに展開する際に、ソフトウェア アプリケーションをインストールすることもできます。  

-   **ワークグループ メンバーシップ**  

     参照コンピューターは、ワークグループのメンバーとして構成する必要があります。  

-   **Sysprep**  

     システムの準備 (Sysprep) ツールは、Windows オペレーティング システムを新しいハードウェアにインストールするときに他の展開ツールと併用できるテクノロジです。 Sysprep は、コンピューターの再起動時に新しいコンピューター セキュリティ識別子 (SID) を作成するようにコンピューターを構成することで、ディスク イメージの作成または顧客への配布のためにコンピューターを準備します。 さらに、Sysprep は、ユーザーおよびコンピューター固有の設定と、対象コンピューターにコピーしてはならないデータを消去します。  

     次のコマンドを実行することにより、参照コンピューターに対して手動で Sysprep を実行することができます。  

     `Sysprep /quiet /generalize /reboot`  

     /generalize オプションは、Windows インストールからシステム固有のデータを削除することを Sysprep に指示します。 システム固有の情報には、イベント ログ、一意なセキュリティ識別子 (SID)、その他の一意の情報が含まれています。 システム固有の情報を削除してから、コンピューターを再起動します。  

     「 [Prepare Windows for Capture](../understand/task-sequence-steps.md#BKMK_PrepareWindowsforCapture) 」タスク シーケンスのステップまたはキャプチャ メディアを使用して、Sysprep を自動化することができます。  

    > [!IMPORTANT]  
    >  「 [Prepare Windows for Capture](../understand/task-sequence-steps.md#BKMK_PrepareWindowsforCapture) 」タスク シーケンス ステップは、Sysprep を実行する前に、参照コンピューターのローカル管理者のパスワードをリセットしようとします。 ローカルのセキュリティ ポリシー [パスワードは、複雑さの要件を満たす必要がある] **** が有効な場合、タスク シーケンス ステップは、管理者パスワードのリセットに失敗します。 この場合は、タスク シーケンスを実行する前にこのポリシーを無効にします。  

     Sysprep について詳しくは、「 [システムの準備 (Sysprep) テクニカル リファレンス](http://go.microsoft.com/fwlink/?LinkId=280286)」をご覧ください。  

-   **インストールのシナリオを軽減するために必要な適切なツールおよびスクリプト**  

     インストールのシナリオを軽減するために必要な適切なツールおよびスクリプト  

-   **壁紙、ブランド、既定のユーザー プロファイルなどのデスクトップの適切なカスタマイズ**  

     参照コンピューターのオペレーティングシステムをキャプチャするときに含めるデスクトップのカスタマイズ プロパティで参照コンピューターを構成できます。 デスクトップのプロパティには、壁紙、組織のブランド、標準の既定ユーザー プロファイルが含まれます。  

##  <a name="a-namebkmkmanuallybuildreferencea-manually-build-a-reference-computer"></a><a name="BKMK_ManuallyBuildReference"></a> 参照コンピューターの手動による構築  
 次の手順を使用して、参照コンピューターを手動で構築します。  

> [!NOTE]  
>  参照コンピューターを手動で構築する場合は、キャプチャ メディアを使用してオペレーティング システム イメージをキャプチャできます。 詳細については、「[キャプチャ メディアを作成する](../deploy-use/create-capture-media.md)」を参照してください。  

#### <a name="to-manually-build-the-reference-computer"></a>参照コンピューターを手動で構築するには  

1.  参照コンピューターとして使用するコンピューターを特定します。  

2.  展開するオペレーティング システム イメージの作成に必要な適切なオペレーティング システムやその他のソフトウェアを使用して、参照コンピューターを構成します。  

    > [!WARNING]  
    >  少なくとも、適切なオペレーティング システムと Service Pack、サポート ドライバー、必要なソフトウェアの更新をインストールします。  

3.  参照コンピューターをワークグループのメンバーとして構成します。  

4.  パスワードの値が空白となるように、参照コンピューターのローカルの管理者パスワードをリセットします。  

5.  **sysprep /quiet /generalize /reboot**コマンドを使用して Sysprep を実行します。 /generalize オプションは、Windows インストールからシステム固有のデータを削除することを Sysprep に指示します。 システム固有の情報には、イベント ログ、一意なセキュリティ識別子 (SID)、その他の一意の情報が含まれています。 システム固有の情報を削除してから、コンピューターを再起動します。  

 参照コンピューターの準備ができた後、タスク シーケンスを使用して、参照コンピューターからオペレーティング システム イメージをキャプチャします。  詳しい手順については、「 [オペレーティング システム イメージを既存の参照コンピューターからキャプチャする](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md#BKMK_CaptureExistingRefComputer)」をご覧ください。  

##  <a name="a-namebkmkusetstobuildreferencea-use-a-task-sequence-to-build-a-reference-computer"></a><a name="BKMK_UseTSToBuildReference"></a> タスク シーケンスによる参照コンピューターの構築  
 オペレーティング システム、ドライバー、アプリケーションなどを展開するタスク シーケンスを使用して、参照コンピューターを作成するプロセスを自動化できます。  以下の手順を使用して参照コンピューターを構築し、その後、参照コンピューターからオペレーティング システム イメージをキャプチャします。  

-   タスク シーケンスを使用して、参照コンピューターからオペレーティング システム イメージを構築し、キャプチャします。  詳しい手順については、「 [Use a task sequence to build and capture a reference computer](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md#BKMK_BuildCaptureTS)」を参照してください。  



<!--HONumber=Nov16_HO1-->

