---
title: ハイブリッド MDM の新機能
titleSuffix: Configuration Manager
description: Configuration Manager と Intune のハイブリッド展開で使用できるモバイル デバイス管理の新機能について説明します。
ms.date: 07/12/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 7b127cee-61f1-4681-9760-caebed36ddf5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d2a705ed8b09e4c2de92baa22164cbe97f180462
ms.sourcegitcommit: e54e9d4a735e72b84095e0017c5bec50af480207
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2018
ms.locfileid: "39039626"
---
# <a name="whats-new-in-hybrid-mobile-device-management-with-configuration-manager-and-microsoft-intune"></a>Configuration Manager と Microsoft Intune を使用したハイブリッド モバイル デバイス管理の新機能

*適用対象: System Center Configuration Manager (Current Branch)*

この記事では、System Center Configuration Manager と Intune のハイブリッド展開で使用できるモバイル デバイス管理 (MDM) の新機能の詳細について説明します。     

> [!Note]    
> Azure 上の Intune は、Microsoft が推奨する MDM ソリューションです。     
> - Intune スタンドアロンの新機能と更新内容の詳細については、「[Microsoft Intune の新機能](https://docs.microsoft.com/intune/whats-new)」を参照してください。    
> - Intune スタンドアロンに移行する詳細な方法については、「[Migrate hybrid MDM users and devices to Intune standalone](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)」(ハイブリッド MDM ユーザーとデバイスを Intune スタンドアロンに移行する) を参照してください。
> - Intune とハイブリッド MDM の UI の更新の詳細については、「[Intune とエンド ユーザー アプリの UI の更新](https://docs.microsoft.com/intune/whats-new-app-ui)」を参照してください。 

##  <a name="compatibility-with-configuration-manager-versions"></a>Configuration Manager のバージョンとの互換性  
この記事の各セクションでは、3 つの異なるカテゴリにあるハイブリッド機能を一覧表示します。 次のガイダンスを使用すると、各カテゴリの機能とさまざまなバージョンの Configuration Manager との互換性を判断できます。  

|機能のカテゴリ|説明|
|-|-|
|**Microsoft Intune の新機能** | 通常、このカテゴリに一覧表示されたすべての機能は、Configuration Manager のすべてのリリースで動作します。 これには System Center 2012 R2 Configuration Manager リリースが含まれています。これらの機能では Intune サービスのみが必要であり、Configuration Manager の追加機能は不要なためです。|
|**Configuration Manager Technical Preview の新機能**| このカテゴリに一覧表示されたすべての機能は、指定されたバージョンの Technical Preview リリースでのみ動作します。 これらの機能を試すには、機能の説明で指定されたバージョンの Technical Preview をインストールする必要があります。 詳細については、「[System Center Configuration Manager の Technical Preview](../../core/get-started/technical-preview.md)」を参照してください。|
|**Configuration Manager (現在のブランチ) の新機能**| このカテゴリに一覧表示されたすべての機能は、バージョン 1511 や 1602 など、指定されたバージョンの Configuration Manager (現在のブランチ) でのみ動作します。 ハイブリッド展開に旧バージョンの Configuration Manager を使用している場合は、機能の説明で指定されたバージョンの Configuration Manager (現在の分岐) にアップグレードする必要があります。 詳細については、「[System Center Configuration Manager へのアップグレード](../../core/servers/deploy/install/upgrade-to-configuration-manager.md)」を参照してください。|



## <a name="july-2018"></a>2018 年 7 月

### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能

#### <a name="support-for-security-enhancement-in-intune-service"></a>Intune サービスでのセキュリティ拡張機能のサポート
<!--2520152--> コンプライアンス ポリシーが割り当てられていないデバイスはハイブリッドで非準拠であると指定できるようになりました。 Azure Portal 上で Intune のこの設定を構成します。 内部リソースをセキュリティで保護するために、この機能を有効にすることを強くお勧めします。

この機能はハイブリッド テナントにおいて既定では無効になっています。 この機能を有効にした場合、コンプライアンス ポリシーが割り当てられていないデバイスは非準拠と見なされます。 また、条件付きアクセスを有効にした場合、これらのデバイスは内部リソースにアクセスできなくなります。 このようなリソースは、環境内の条件付きアクセス ポリシーに基づいて、Outlook の場合もあれば SharePoint の場合もあります。 この設定をオフのままとした場合、これらのデバイスは引き続き現在と同じレベルのアクセス権を保持します。

この機能を有効にした場合にどのような影響があるかを判断するのに役立つように、Microsoft では [TechNet ギャラリーにスクリプト](https://gallery.technet.microsoft.com/SQL-Query-for-Hybrid-MDM-5bcb8695)を提供しています。 Configuration Manager データベースに対してこのスクリプトを実行すると、コンプライアンス ポリシーの対象となっていないデバイスが一覧表示されます。

詳細については、以下の記事を参照してください。
- [Intune サービスでのセキュリティ拡張機能](https://aka.ms/compliance_policies)に関するブログ記事 
- [Configuration Manager でのデバイス コンプライアンス ポリシー](/sccm/mdm/deploy-use/device-compliance-policies)

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app"></a>ポータル サイト アプリの非対応メッセージへの更新 
<!--1832222--> 非対応デバイスのユーザーに表示されるメッセージを修正しています。 メッセージの意味は同じですが、よりわかりやすく、技術的な専門用語が少ない言い方に変更されます。 また、最新の状態を保持するためにドキュメントと修復の手順へのリンクを更新しています。  

次の前後のテキストは、表示されるメッセージの改善例の 1 つを示しています。  

- 前: "*このデバイスは、IT 管理者によって要求された指定の期間に Intune サービスに接続していません。この問題を解決するためには、デバイスでポータル サイト アプリを開いて [コンプライアンスの確認] ボタンをクリックしてください。*"  

- 後: "*お使いのデバイスはしばらくの間、組織にチェックインされていません。接続を再確立するには、デバイスでポータル サイト アプリを開き、[設定の確認] をタップします。*"  

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings"></a>[職場または学校にアクセスする] 設定を使用したデバイス カテゴリの選択 
<!--1058963--> [デバイス グループ マッピング](https://docs.microsoft.com/intune/device-group-mapping)を有効にした場合、Windows 10 のユーザーは、**[設定]** > **[アカウント]** > **[職場または学校にアクセスする]** の **[接続]** から登録した後に、デバイス カテゴリの選択を求められます。  



## <a name="june-2018"></a>2018 年 6 月

### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能

#### <a name="access-to-macos-company-portal-pre-release-build"></a>macOS ポータル サイトのプレリリース ビルドへのアクセス 
<!--1734766--> Microsoft AutoUpdate を使用して、Insider Program に参加することにより、早期にビルドを受け取るためにサインアップします。 サインアップすると、エンド ユーザーが使用できるようになる前に更新されたポータル サイトを使用できます。

#### <a name="intune-app-protection-policies-and-microsoft-edge"></a>Intune アプリ保護ポリシーと Microsoft Edge 
<!--1818968,1818969--> モバイル デバイス (iOS と Android) 向けの Microsoft Edge ブラウザーが Microsoft Intune アプリ保護ポリシー対応になりました。 iOS デバイスか Android デバイスの利用者が Edge アプリケーションで企業 Azure Active Directory アカウントを利用してサインインすると、Intune によって保護されます。 iOS デバイスの場合、**[Require managed browser for web content]\(Web コンテンツに Managed Browser を要求する\)** ポリシーによって、Edge が管理されているとき、Edge でリンクを開くことができます。



## <a name="may-2018"></a>2018 年 5 月

### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能

#### <a name="requesting-help-in-the-company-portal-for-windows-10"></a>Windows 10 ポータル サイト でのヘルプの要求 
<!--1874137--> Windows 10 のポータル サイトでは、ユーザーが問題のヘルプを入手するワークフローを開始した時点で、アプリ ログ ファイルを直接 Microsoft に送信するようになりました。 この動作によって、Microsoft に発生した問題をトラブルシューティングして解決しやすくなりました。  


### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager (現在のブランチ) の新機能

#### <a name="android-for-work-and-lookout-onboarding-moved-to-intune-on-azure"></a>Android for Work と Lookout のオンボーディングが Azure の Intune に移動
<!--2355022,2357366--> Intune の最新更新プログラムを適用すると、Azure Portal の Intune のハイブリッド モバイル デバイス管理で、Android for Work 統合と Lookout Mobile Threat Defense 統合を有効にし、管理できます。 この更新プログラムが公開される前は、Intune Classic (Silverlight) ポータルでのみこれらの統合を構成できました。
 
注: Lookout は、ハイブリッドでサポートされている唯一の Mobile Threat Defense (MTD) プロバイダーです。 以前に他の MTD プロバイダーと統合していた場合、Azure Portal の Intune に引き続き表示されます。 そのコネクタを削除した場合、再び追加することはできません。
 
これらの変更は、既存の機能には影響を与えません。 関連するアプリ、レポート、ポリシーの管理には、引き続き Configuration Manager コンソールを使用します。
 
詳細については、以下の記事を参照してください。
- [Android ハイブリッド デバイスの管理をセットアップする](/sccm/mdm/deploy-use/enroll-hybrid-android)
- [デバイス、ネットワーク、アプリケーションのリスクに基づき、会社のリソースへのアクセスを管理する](/sccm/mdm/deploy-use/lookout-mobile-threat-defense-in-configuration-manager)


#### <a name="support-for-new-versions-of-cisco-anyconnect-client-for-ios"></a>iOS 用 Cisco AnyConnect クライアントの新しいバージョンのサポート
<!--1357393--> iOS バージョン 4.0.7 以降の Cisco AnyConnect のサポートを有効にすることができます。 有効にした場合、既存の Cisco AnyConnect VPN プロファイルには **Cisco Legacy AnyConnect** というラベルが付けられ、引き続き従来どおり動作します。 **Cisco AnyConnect** オプションは、iOS バージョン 4.0.7 以降の Cisco AnyConnect で動作する新しい VPN プロファイル用です。

  > [!Tip]  
  > iOS 向け Cisco AnyConnect 4.0.07x 以降は、最初はバージョン 1802 で[プレリリース機能](/sccm/core/servers/manage/pre-release-features)として導入されました。 バージョン 1802 に対する[更新 4163547](https://support.microsoft.com/help/4163547) 以降、この機能はプレリリース機能ではなくなりました。  

> [!Note]  
> macOS VPN プロファイルでは、引き続き **Cisco Legacy AnyConnect** オプションを使用します。 



## <a name="april-2018"></a>2018 年 4 月

### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10"></a>Intune は、Windows 10 のポータル サイト アプリの Fluent Design System に適合します。 
<!--1195010--> Windows 10 の Intune ポータル サイト アプリは、[Fluent Design System のナビゲーション ビュー](/windows/uwp/design/basics/navigation-basics)で更新済みです。 アプリの側面に沿って、すべての最上位ページの静的な一覧が縦方向に表示されることがわかります。 任意のリンクをすばやくクリックして、ページの閲覧やページ間の切り替えを行います。 この更新プログラムは、Intune により適応しやすく、親しみやすい、使い慣れたエクスペリエンスを作成するための継続的な取り組みの一環として提供されている、いくつかの試みの 1 つです。 更新後の外観を確認するには、[アプリの UI の新機能](/intune/whats-new-app-ui)に関するページを参照してください。

#### <a name="improved-device-tiles-in-the-windows-10-company-portal"></a>Windows 10 ポータル サイトのデバイス タイルの改善
<!--2213364--> 視覚障碍のあるユーザーにより簡単にお使いいただけるように、また、画面読み取りツールのパフォーマンスを向上させるためにタイルが更新されました。


#### <a name="test-the-company-portal-for-macos-on-virtual-machines"></a>仮想マシンでの macOS 用ポータル サイトのテスト
<!--2216679--> IT 管理者が Parallels Desktop と VMware Fusion の仮想マシンで macOS 用ポータル サイト アプリをテストする際に役立つガイダンスを公開しました。 詳細については、「[テスト用に仮想 macOS マシンを登録する](/intune/macos-enroll#enroll-virtual-macos-machines-for-testing)」を参照してください。


#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos"></a>macOS 用ポータル サイト アプリでの診断レポートの送信
<!--2216677--> macOS デバイス用ポータル サイト アプリが更新され、ユーザーが Intune に関連するエラーを報告する方法が改善されました。 ポータル サイト アプリから、従業員は次の操作を行うことができます。

- Microsoft 開発者チームに直接診断レポートをアップロードする。
- 会社の IT サポート チームにインシデント ID をメールで送信する。


#### <a name="updated-help-experience-on-company-portal-app-for-android"></a>Android 用ポータル サイト アプリの更新されたヘルプ エクスペリエンス 
<!--1631531--> Android プラットフォームのベスト プラクティスに合うように Android 用ポータル サイト アプリのヘルプ エクスペリエンスを更新しました。 ユーザーがアプリで問題に直面したとき、**[メニュー]** > **[ヘルプ]** をタップしてから、次を行うことができるようになりました。
- 診断ログを Microsoft にアップロードします。
- 問題とインシデント ID を記載した電子メールを会社のサポート担当者に送信します。


#### <a name="update-where-to-configure-your-app-protection-policies"></a>アプリの保護ポリシーを構成する場所を更新 
<!--2144597--> Microsoft Intune サービス内の Azure Portal で、ユーザーが一時的に **[Intune App Protection]** サービス ブレードから **[モバイル アプリ]** ブレードにリダイレクトされます。 すべてのアプリ保護ポリシーが Intune のアプリ構成の **[モバイル アプリ]** ブレードに既に置かれていることに注意してください。 Intune App Protection に移動する代わりに、Intune に移動します。 2018 年 4 月にリダイレクトを停止し、**[Intune App Protection]** サービス ブレードを完全に削除する予定です。したがって、Intune 内のアプリ保護ポリシーのための場所は 1 つだけになります。 

**ユーザーへの影響** この変更は、Intune スタンドアロンのお客様とハイブリッド (Intune と Configuration Manager) のお客様の両方に影響します。 この統合は、クラウド管理の簡素化に役立ちます。

**この変更に対して必要な準備** **[Intune App Protection]** サービス ブレードの代わりに **Intune** をお気に入りとして登録し、Intune の **[モバイル アプリ]** ブレードのアプリ保護ポリシーのワークフローを習熟してください。 リダイレクトを短期間行い、その後 **[Intune App Protection]** ブレードを削除します。 すべてのアプリ保護ポリシーは既に Intune にあり、どの条件付きアクセス ポリシーでも変更できることを忘れないでください。 条件付きアクセス ポリシーの変更について詳しくは、「[Azure Active Directory の条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)」をご覧ください。 その他の情報については、「[アプリ保護ポリシーとは](/intune/app-protection-policy)」をご覧ください。 




#### <a name="user-experience-update-for-the-company-portal-app-for-ios"></a>iOS 用ポータル サイト アプリに関するユーザー エクスペリエンスの更新プログラム 
<!--1412866--> iOS 用のポータル サイト アプリに対して、主要なユーザー エクスペリエンスの更新プログラムをリリースしました。 この更新プログラムでは、ビジュアル面の完全な再設計により、最新の外観に一新されています。 アプリの機能が更新されていますが、その使いやすさとアクセシビリティも向上しています。  

次の点も改善されています。
- iPhone X のサポート。
- アプリの起動時間と応答の読み込み時間の短縮。
- 最新の状態情報をユーザーに提供する追加の進行状況バー。
- 物事が正しく進まなかった場合、それを報告しやすくするためのログのアップロード方法の向上。  

新しい外観を確認するには、[アプリの UI の新機能](/intune/whats-new-app-ui)に関するページを参照してください。



## <a name="march-2018"></a>2018 年 3 月

### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能

#### <a name="windows-company-portal-send-feedback-option-may-no-longer-work"></a>Windows ポータル サイトの [フィードバックの送信] オプションは今後機能しない場合がある
<!--2070166--> Windows ポータル サイト アプリには、アプリに関するフィードバックを Microsoft に送信できるように 'フィードバックの送信' オプションがあります。 2018 年 4 月 30 日から、Windows 10 バージョン 1607 以降を実行している Windows 10 ポータル サイト アプリでのみ、このオプションが引き続きサポートされます。   

**ユーザーへの影響**

エンド ユーザーに Windows ポータル サイト アプリをインストールしていない場合、このメッセージは無視してください。

エンド ユーザーの中にポータル サイト アプリをインストールしている人がいる場合、次のシナリオにおいて、4 月 30 日から 'フィードバックの送信' ボタンが機能しなくなることに注意してください。  

 - Windows 10 バージョン 1507 とバージョン 1511 の Windows 10 ポータル サイト アプリ  

 - Windows Phone Windows 8.1 ポータル サイト アプリ  

影響を受けるデバイスの場合、'フィードバックの送信' オプションは機能せず、再試行でも動作しません。 影響を受けるデバイスで発生した現象について Microsoft にフィードバックを送信するには、下に記す代替フィードバック チャネルをご利用ください。

**この変更に対して必要な準備**

エンド ユーザーにこの変更を通知し、必要に応じてユーザー ガイダンスを更新してください。 

Windows Phone 8.1、Windows 10 バージョン 1507、Windows 10 バージョン 1511 でポータル サイトを利用しているエンド ユーザーに 2 つの代替フィードバック チャネルを利用できることをお知らせください。 代替フィードバック方法:  

- Windows 10 でフィードバック ハブ アプリを使用する  
- WinCPfeedback@microsoft.com に電子メールを送信する  

Windows 10 バージョン 1607 以降を利用しているエンド ユーザーに Microsoft Store で入手できる Windows ポータル サイトの最新版に更新するように要請します。



#### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview"></a>Azure Active Directory の Web サイトでは、Intune Managed Browser アプリを要求し、Managed Browser (パブリック プレビュー) に対するシングル サインオンをサポートすることができる
<!-- 710595 --> Azure Active Directory (Azure AD) を使用している場合、モバイル デバイスでの Web サイトへのアクセスを Intune Managed Browser アプリに制限できるようになりました。 Managed Browser では、Web サイトのデータは安全性を維持され、エンド ユーザーの個人データと分離されます。 さらに、Managed Browser は、Azure AD によって保護されているサイトに対するシングル サインオン機能をサポートします。 Managed Browser にサインインすると、または Intune によって管理されている別のアプリでデバイスの Managed Browser を使うと、ユーザーが資格情報を入力しなくても、Managed Browser は Azure AD によって保護されている会社サイトにアクセスできます。 この機能は、Outlook Web Access (OWA) や SharePoint Online などのサイトだけでなく、Azure App プロキシ経由でアクセスされるイントラネット リソースのような他の企業サイトにも適用されます。



## <a name="february-2018"></a>2018 年 2 月

### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能

- **デバイス登録マネージャーを使う登録の macOS ポータル サイトによるサポート**  
    ユーザーは、macOS ポータル サイトで登録するときに、デバイス登録マネージャーを使うことができるようになりました。
    <!-- 1352411 -->


## <a name="january-2018"></a>2018 年 1 月

### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能

- **Android for Work のポータル サイト アプリの承認**  
  Android for Work を使用している組織は、Android 用のポータル サイト アプリを手動で承認します。 その後、管理された Google Play ストアから引き続き自動更新を受信します。
  <!--1797090 -->  

- **Intune の条件付きアクセス ポリシーは、Azure Portal からのみ利用できる**   
  このリリース以降は、**[Azure Active Directory]** > **[条件付きアクセス]** から [Azure Portal](https://portal.azure.com) の条件付きアクセス ポリシーを構成して管理する必要があります。 便宜上、**[Intune]** > **[条件付きアクセス]** の、Azure Portal 内にある Intune からこのブレードにアクセスすることもできます。
  <!-- 1737088 1634311 --> 

- **コンプライアンス メールの更新**    
  コンプライアンス違反のデバイスを報告するメールが送信される際に、そのコンプライアンス違反のデバイスの詳細が含まれます。 
  <!--1637547 -->

- **Android デバイスの "解決" アクションの新しい機能**    
  Android 用ポータル サイト アプリは、[デバイス暗号化の問題](https://docs.microsoft.com/intune-user-help/encrypt-your-device-android)を解決するために、**[デバイス設定の更新]** の "解決" アクションを拡張しています。
  <!--1583480-->

- **Windows 10 向けポータル サイト アプリで利用できるリモート ロック**    
  エンドユーザーは、Windows 10 向けポータル サイト アプリから自分のデバイスをリモートでロックできるようになりました。 このアクションはエンド ユーザーがアクティブに使用しているローカル デバイスには表示されません。
  <!--676506-->

- **Windows 10 向けポータル サイト アプリの準拠に関する問題を容易に解決できる**   
  Windows デバイスを使用するエンド ユーザーは、ポータル サイト アプリ内で非準拠の理由をタップできます。 可能な場合には、問題を解決するために設定アプリの適切な場所に直接移動します。
  <!--676546-->    



## <a name="december-2017"></a>2017 年 12 月

### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能

- **利用可能なアプリケーションの展開で Android Enterprise がサポートされるようになりました**    
  Android Enterprise (旧称 Android for Work) アプリを、**必須**に加えて、**利用可能**として展開できるようになりました。 詳細については、「[System Center Configuration Manager で Android アプリケーションを作成する](/sccm/mdm/deploy-use/creating-android-applications)」を参照してください。



## <a name="november-2017"></a>2017 年 11 月

### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能

- 
    **管理対象アプリから許可されているテキスト プロトコル**  
  Intune App SDK によって管理されているアプリは、SMS メッセージを送信できます。
<!-- 1414050  -->   

- **macOS 用ポータル サイト アプリ提供開始**   
  macOS での Intune ポータル サイトのエクスペリエンスが更新されました。 ユーザーが登録済みのすべてのデバイスで必要となるすべての情報とコンプライアンス通知が明確に表示されるように最適化されています。 Intune ポータル サイトがデバイスに展開されると、macOS 用の Microsoft AutoUpdate によって更新プログラムが提供されます。 macOS デバイスから Intune ポータル サイトにログインすることで、新しい macOS 用 Intune ポータル サイトをダウンロードします。
  <!--1541700-->   

- **Microsoft Planner が承認済みアプリのモバイル アプリ管理 (MAM) リストの一部に**    
  iOS および Android 用の Microsoft Planner アプリが、モバイル アプリ管理 (MAM) に対する承認済みアプリの一部となりました。 Azure Portal の Intune App Protection ブレードからすべてのテナントに対してアプリを構成します。 詳細については、[承認済みアプリの MAM リスト](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)に関するページをご覧ください。
  <!-- 1248473 -->    

- 
    **iOS の管理対象アプリ ログにアクセス**    
  Managed Browser をインストールしているエンド ユーザーは、Microsoft が公開したすべてのアプリの管理状態を表示し、管理対象 iOS アプリの問題を解消するためにログを送信できるようになりました。
<!-- 1469920 -->    

  iOS デバイスの Managed Browser でトラブルシューティング モードを有効にする方法については、「[iOS で Managed Browser を使用し、管理対象アプリ ログにアクセスする方法](https://docs.microsoft.com/intune/app-configuration-managed-browser#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios)」を参照してください。

- **iOS 用ポータル サイト バージョン 2.9.0 でのデバイスのセットアップ ワークフローの機能強化**    
  iOS 用ポータル サイト アプリでのデバイス セットアップ ワークフローを改善しました。 言葉がよりわかりやすくなり、可能な範囲で画面をまとめました。 また、セットアップのテキスト全体でお客様の会社名を使用することで、表現がより会社に合ったものになっています。 この更新されたワークフローについては、「[アプリの UI の新機能](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-november-13-2017)」ページで確認できます。

- **Android 用ポータル サイト アプリに関するフィードバック プロンプト**    
  Android 用ポータル サイト アプリからエンド ユーザー フィードバックを要求されるようになりました。 このフィードバックは Microsoft に直接送信され、エンドユーザーは一般の Google Play ストアでアプリをレビューできます。 フィードバックは必須ではなく、ユーザーは簡単にこれを拒否して、アプリの使用を続行できます。 
  <!--1165249-->    

- **Windows 10 デバイスで確認できるデバイス情報のエンドユーザーへの通知**    
  Windows 10 用ポータル サイト アプリの [デバイスの詳細] 画面に **[所有権の種類]** が追加されました。 この情報により、ユーザーは Intune のエンド ユーザー ドキュメントから直接プライバシーの詳細を参照できます。この情報は、**[バージョン情報]** 画面でも確認できます。
  <!--1337920-->    

- **Android デバイスで利用できる新しい '解決' アクション**    
  Android のポータル サイト アプリの _[デバイス設定の更新]_ ページに '解決' アクションが導入されます。 このオプションを選択すると、デバイスの非準拠の原因になっている設定に、エンド ユーザーが直接誘導されます。 Android 向けのポータル サイト アプリでは現在のところ、[デバイス パスコード](https://docs.microsoft.com/intune-user-help/set-your-pin-or-password-android)、[デバイスの暗号化](https://docs.microsoft.com/intune-user-help/encrypt-your-device-android)、[USB デバッグ](https://docs.microsoft.com/intune-user-help/you-need-to-turn-off-usb-debugging-android)、[不明なソース](https://docs.microsoft.com/intune-user-help/you-need-to-turn-off-unknown-sources-android)設定に対してこのアクションがサポートされています。 
  <!--1583480-->    


### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager (現在のブランチ) の新機能

- **コンプライアンス非対応に対するアクション**    
  コンプライアンスに対応していないデバイスに適用される時間順のアクションを構成できるようになりました。 たとえば、コンプライアンスに対応していないデバイスをユーザーに電子メールで通知したり、そのようなデバイスにコンプライアンス非対応とマークしたりすることができます。 詳細については、「[コンプライアンス非対応に対するアクションの設定](/sccm/mdm/deploy-use/actions-for-noncompliance)」を参照してください。
  <!--1321366 -->

- **新しいモバイル アプリケーション管理ポリシーの設定**     
  次の設定がモバイル アプリケーション管理ポリシーの設定に追加されました。
  - **連絡先の同期を無効にする:** アプリでデバイス上のネイティブ連絡先アプリにデータを保存できなくなります。
  - **印刷を無効にする:** アプリで職場または学校のデータを印刷できなくなります。
  <!-- 1324760 -->    

  「[Configuration Manager のモバイル アプリケーション管理ポリシーを使ったアプリの保護](/sccm/mdm/deploy-use/protect-apps-using-mam-policies)」を参照し、新しいアプリの保護のポリシー設定を試してください。

- **Windows 10 ARM64 デバイスのサポート**     
  Windows 10 を実行する ARM64 デバイスを使用できるようになると、それらのデバイスでハイブリッド モバイル デバイス管理 (MDM) シナリオがサポートされます。 詳細については、「[Windows 10 ARM64 デバイスのサポート](/sccm/core/plan-design/changes/whats-new-in-version-1710#windows-10-arm64-device-support)」をご覧ください。
  <!-- 1355000 -->    

- **Configuration Manager コンソールの VPN プロファイル エクスペリエンスの向上**     
  このリリースでは、選択したプラットフォームに適した設定が表示されるように、VPN プロファイル ウィザードとプロパティ ページが更新されました。 この機能は、以前は Configuration Manager Technical Preview 1709 で使用できました。 現在は、Intune と Configuration Manager (Current Branch) バージョン 1710 のハイブリッド展開で使用できます。 詳しくは、「[Configuration Manager コンソールの VPN プロファイル エクスペリエンスの向上](/sccm/core/plan-design/changes/whats-new-in-version-1710#improved-vpn-profile-experience-in-configuration-manager-console)」をご覧ください。
  <!-- 1318232 -->


### <a name="new-in-configuration-manger-technical-preview-1711"></a>Configuration Manager Technical Preview 1711 の新機能

- **Windows 10 用の新しいコンプライアンス ポリシー オプション**   
  Windows 10 デバイスのコンプライアンス ポリシーに新しいオプションを構成できるようになりました。 新しい設定には、ファイアウォール、ユーザー アカウント制御、Windows Defender Anitivirus、OS ビルド バージョン管理に関するポリシーがあります。 詳細については、「[Windows 10 用の新しいコンプライアンス ポリシー オプション](/sccm/core/get-started/capabilities-in-technical-preview-1711#new-compliance-policy-options-for-windows-10)」をご覧ください。



## <a name="october-2017"></a>2017 年 10 月

### <a name="new-in-configuration-manager-technical-preview-1709"></a>Configuration Manager Technical Preview 1709 の新機能

- **Configuration Manager コンソールの向上した VPN プロファイル エクスペリエンス**      
  VPN プロファイルの設定は、プラットフォームに従ってフィルター処理されるようになりました。 新しい VPN プロファイルを作成するとき、サポートされているプラットフォームのそれぞれに適した設定のみが選択されます。 既存の VPN プロファイルには影響しません。 この変更の詳細については、[こちら](/sccm/core/get-started/capabilities-in-technical-preview-1709#improved-vpn-profile-experience-in-configuration-manager-console)をご覧ください。
  <!-- 1313282 -->


### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能  

- **Android 向けポータル サイト アプリに関してユーザーの自己解決をサポートする**     
  Android 向けポータル サイト アプリでは、エンド ユーザーへの指示が追加されています。それは新しいユース ケースの理解や、可能な場合にはその自己解決にも役立ちます。
    - エンド ユーザーは、追加が許されているデバイスの最大数に達した場合、デバイスを削除するように [Azure Active Directory ポータル](https://account.activedirectory.windowsazure.com/r/#/profile)に誘導されます。
    - [Samsung Knox デバイスのアクティベーション エラーを解消する](https://go.microsoft.com/fwlink/?linkid=859718)か、[節電モードをオフにする](https://docs.microsoft.com/intune-user-help/power-saving-mode-android)ための手順がエンド ユーザーに表示されます。 いずれの解決策でも問題が解消されない場合、[Microsoft にログを送信する](https://docs.microsoft.com/intune-user-help/send-logs-to-microsoft-android)方法を説明します。
  <!-- 1573324, 1573150, 1558616, 1564878 -->      

- **Android 用ポータル サイトのデバイスのセットアップ進行状況インジケーター**    
  Android 用ポータル サイト アプリでは、ユーザーがデバイスを登録しているときに、デバイスのセットアップ進行状況インジケーターが示されます。 このインジケーターで新しいステータスが表示されます。初めに表示されるものから挙げると、[デバイスをセットアップしています...]、[デバイスを登録しています]、[デバイスの登録を終了しています]、[デバイスのセットアップを終了しています] です。  
  <!--1565657-->    

- **iOS 用ポータル サイトでの証明書ベースの認証のサポート**    
  iOS 用ポータル サイト アプリでの証明書ベースの認証 (CBA) のサポートが追加されました。 CBA を使用するユーザーは、ユーザー名を入力してから [Sign in with a certificate]\(証明書でサインイン\) リンクをタップします。 Android および Windows 用ポータル サイト アプリでは、既に CBA がサポートされています。 詳細については、[ポータル サイト アプリにサインインする](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)方法に関するページをご覧ください。
  <!--1029830-->   

- **ポータル サイトのデバイスのセットアップ ワークフローを改善**     
  Android 用ポータル サイト アプリにおけるデバイスのセットアップ ワークフローを改善しました。 言語がよりわかりやすく、会社固有のものとなり、可能な範囲で画面をまとめるようにしました。 これらの機能強化は、[アプリ UI の新機能](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-october-2-2017)に関するページで確認できます。
  <!--1490692-->     

- **Android デバイスの連絡先情報へのアクセスを要求するガイダンスを改善**     
  Android 用ポータル サイト アプリでは、エンド ユーザーに対して連絡先情報へのアクセス許可を求めることがあります。 エンド ユーザーがこのアクセスを拒否した場合に、条件付きアクセスを許可するよう求めるアプリ内通知が表示されます。 
  <!--1484985-->     

- **Android 用に安全なスタートアップ修復**     
  Android デバイスを使用するエンド ユーザーは、ポータル サイト アプリ内で非準拠の理由をタップできます。 可能な場合には、問題を解決するために設定アプリの適切な場所に直接移動します。 
  <!--1490712-->    

- **Android Oreo 用ポータル サイト アプリでのエンド ユーザー向けの追加のプッシュ通知**    
  Android Oreo 用のポータル サイト アプリがバック グラウンド タスク (Intune サービスからポリシーを取得するなど) を実行しているときに、エンド ユーザーに知らせる追加の通知が表示されます。 この通知により、ポータル サイトがデバイス上でいつ管理タスクを実行しているかが、エンド ユーザーにとってより分かりやすくなります。 この機能強化は、Android Oreo 用のポータル サイト アプリの[ポータル サイト UI の全体的な最適化](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)の一部です。 
  <!--1475932 -->     

- **仕事用プロファイルを使用した場合の Android 用ポータル サイト アプリの新しい動作**     
  仕事用プロファイルを使用して Android for Work デバイスを登録した場合は、仕事用プロファイルのポータル サイト アプリでデバイスの管理タスクが実行されます。 

  個人用プロファイルの MAM が有効なアプリを使用している場合を除いては、Android 用ポータル サイト アプリを使用することはなくなります。 仕事用プロファイルが正常に登録されると、仕事用プロファイル エクスペリエンスを向上させるために Intune が自動で個人用ポータル サイト アプリを非表示にします。

  Android 用ポータル サイト アプリは、ブラウザーで [Play ストアのポータル サイト](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)を表示して **[有効]** をタップすれば、いつでも個人用プロファイル内で有効化できます。
  <!--1485783-->    

- **維持モードに移行中の Windows 8.1 および Windows Phone 8.1 用ポータル サイト**    
  Windows 8.1 および Windows Phone 8.1 用ポータル サイト アプリが維持モードに移行中であることを知らせる通知が追加されました。 詳細については、「[通知](#notices)」をご覧ください。  
  <!--1428681-->    

- **サポートされていない Samsung Knox デバイスの登録をブロック**   
  ポータル サイト アプリは、サポートされている Samsung Knox デバイスのみを登録しようとします。 MDM 登録を妨げる KNOX のアクティベーション エラーを回避するため、デバイス登録はそのデバイスが [Samsung が公開しているデバイス一覧](https://www.samsungknox.com/knox-supported-devices/knox-workspace)にある場合のみ実行されます。 KNOX をサポートしている Samsung デバイスにはモデル番号がありますが、サポートしていないデバイスにはありません。 使用するデバイスが Knox に対応しているかどうかを、デバイスを購入したり展開したりする前に販売店に確認してください。 対応しているデバイスの一覧は、[Android および Samsung KNOX Standard ポリシー設定](https://docs.microsoft.com/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune#supported-samsung-knox-standard-devices)に関するページで確認できます。
  <!-- 1490695 -->     

- **Android 4.3 以前のサポートを終了**     
  Android 4.3 以前のサポートが終了したことを知らせる通知が追加されました。 詳細については、「[通知](#notices)」をご覧ください。
  <!--1171126, 1326920 -->     

- **登録済みデバイスでどのようなデバイス情報を表示できるかをエンド ユーザーに通知**     
  すべてのポータル サイト アプリの [デバイスの詳細] 画面に、**[所有権の種類]** が追加されます。 この情報により、[会社が確認できる情報](https://docs.microsoft.com/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)に関するページから直接、プライバシーの詳細を確認できるようになります。 この機能強化は、近日中にすべてのポータル サイト アプリに展開される予定です。 iOS 用のこの機能については [9 月](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)にお知らせしました。 
  <!--1165314-->     



## <a name="september-2017"></a>2017 年 9 月

### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能     

- **Windows 10 のポータル サイト アプリに更新アクションが追加されました**    
    Windows 10 向けの会社ポータル アプリでは、ユーザーがプルして更新するか、デスクトップで F5 キーを押して、アプリのデータを更新できます。
    <!-- 1132468 -->     

- **iOS でどのようなデバイス情報を表示できるかをエンド ユーザーに通知**   
    iOS 用のポータル サイト アプリの [デバイスの詳細] 画面に **[所有権の種類]** が追加されました。 この情報により、ユーザーは Intune のエンド ユーザー ドキュメントから直接プライバシーの詳細を参照できます。この情報は、[バージョン情報] 画面でも確認できます。 
    <!--739894-->    

- **Android 用ポータル サイト アプリの文言の分かりやすさの向上**   
    Android 用ポータル サイト アプリの登録プロセスが簡略化されました。テキストが新しくなり、エンド ユーザーがより簡単に登録できるようになりました。 カスタム登録ドキュメントをお持ちの場合は、ドキュメントを更新して新しい画面を反映してください。 「[Intune とエンド ユーザー アプリの UI の更新](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-september-11-2017)」のページにサンプル画像があります。
    <!---1396349-->    

- **Windows Information Protection 許可ポリシーに Windows 10 のポータル サイト アプリを追加**    
    Windows 情報保護 (WIP) をサポートするために、Windows 10 のポータル サイト アプリが更新されました。 WIP 許可ポリシーにアプリを追加できます。 この変更により、アプリを **[適用除外]** 一覧に追加する必要がなくなります。 

    1 つの WIP 構成アイテムのみをデバイスに配信できます。 2 つの WIP 構成アイテムの対象が同じデバイスになっている場合、いずれの WIP ポリシーも適用されません。
    <!-- 677129 -->    

- **iOS 8.0 のサポート終了の通知を追加**    
    iOS 8.0 のサポート終了の通知が追加されました。 詳細については、「[通知](#notices)」をご覧ください。



## <a name="august-2017"></a>2017 年 8 月

### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能     

- **Android ポータル サイト ユーザーおよびアプリ保護ポリシー ユーザーの新しいサインイン エクスペリエンス**    
  エンドユーザーは、Android デバイスを登録しなくても、Android ポータル サイト アプリを使用して、今すぐにアプリを閲覧したり、デバイスを管理したり、IT 連絡先情報を確認したりできます。 さらに、エンド ユーザーが既に Intune App Protection ポリシーによって保護されているアプリを使用し、Android ポータル サイトを起動している場合、エンド ユーザーがデバイスの登録を要求されることはありません。
  <!-- 621669 -->



## <a name="july-2017"></a>2017 年 7 月

### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能

- **Android および Windows Phone のサポート終了に関する通知の追加**    
    Android と Windows Phone のバージョンのサポート終了に関する通知が新たに追加されました。 詳細については、「[通知](#notices)」をご覧ください。


### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager (現在のブランチ) の新機能

以下の機能は以前、Configuration Manager Technical Preview リリースで利用できました。 現在は、Intune と Configuration Manager (Current Branch) バージョン 1706 のハイブリッド展開で使用できます。

- [Entrust 証明機関の Entrust のサポート](/sccm/core/get-started/capabilities-in-technical-preview-1706#support-for-entrust-certification-authorities)
- [新しいモバイル アプリケーション管理ポリシーの設定](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-mobile-application-management-policy-settings)
- [Android for Work の共有構成の更新](/sccm/core/plan-design/changes/whats-new-in-version-1706#updates-to-android-for-work-sharing-configuration)
- [新しいデバイス コンプライアンス ポリシー ルール](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-device-compliance-policy-rules)
- 
  [Configuration Manager クライアントを使用して管理されていない Windows 10 デバイスの新しい構成設定](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-configuration-settings-for-windows-10-devices-that-are-not-managed-with-the-configuration-manager-client)
- [macOS VPN プロファイルの Cisco (IPsec) のサポート](/sccm/core/get-started/capabilities-in-technical-preview-1706#cisco-ipsec-support-for-macos-vpn-profiles)
- [Android および iOS の登録制限](/sccm/core/plan-design/changes/whats-new-in-version-1706#android-and-ios-enrollment-restrictions) 



## <a name="june-2017"></a>2017 年 6 月

### <a name="new-in-microsoft-intune"></a>Microsoft Intune の新機能

- **MDM 機関を変更する**    
  Configuration Manager バージョン 1610 以降では、Microsoft サポートに連絡しなくても、MDM 機関を変更できます。 また、既存のマネージド デバイスの登録を解除してから再登録する必要もありません。 詳細については、「[Change your MDM authority](/sccm/mdm/deploy-use/change-mdm-authority)」(MDM 機関を変更する) を参照してください。

- 
    **管理対象ブラウザーとアプリケーション プロキシの統合**    
Intune Managed Browser は、ユーザーがリモートで作業している場合でも内部の Web サイトにアクセスできるように、Azure AD アプリケーション プロキシ サービスに統合できるようになりました。 ブラウザーのユーザーが、通常通りにサイトの URL を入力すると、Managed Browser がアプリケーション プロキシの Web ゲートウェイを介して要求をルーティングします。 詳細については、「[Managed Browser ポリシーを使用したインターネット アクセスの管理](https://docs.microsoft.com/intune/app-configuration-managed-browser)」を参照してください。

- **Android 用ポータル サイト アプリのアプリの保護ポリシーのエンド ユーザー エクスペリエンスが新しくなりました**  
  お客様のフィードバックに基づいて、Android 用ポータル サイト アプリを変更し、**[会社のコンテンツにアクセスする]** ボタンを表示しました。 目的は、エンド ユーザーがアプリの保護ポリシーをサポートするアプリ、Intune モバイル アプリケーション管理の機能にのみアクセスする必要があるときに、不要な登録プロセスを経由せずに済むようにすることです。 これらの変更は、[アプリ UI の新機能](https://docs.microsoft.com/intune/whats-new-app-ui)ページで確認できます。

- **ポータル サイトを簡単に削除するための新しいメニュー操作**  
  ユーザーからのフィードバックに基づき、Android 用ポータル サイト アプリで、デバイスからのポータル サイトの削除を開始する新しいメニュー操作を追加しました。 この操作は、ユーザーがデバイスからアプリを削除できるように、Intune の管理からデバイスを削除します。 これらの変更は、[アプリ UI の新機能](https://docs.microsoft.com/intune/whats-new-app-ui)ページおよび [Android エンドユーザー文書](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android)で確認できます。

- **アプリを Windows 10 Creators Update と同期するための機能強化**  
  Windows 10 用のポータル サイト アプリが、Windows 10 Creators Update (バージョン 1703) が搭載されたデバイスのアプリ インストール要求の同期を自動的に開始するようになりました。 この動作により、"同期保留中" 状態のときにアプリのインストールが停止する問題が減少します。 また、ユーザーは、アプリ内からの同期を手動で開始することができます。 これらの変更は、[アプリ UI の新機能](https://docs.microsoft.com/intune/whats-new-app-ui)ページで確認できます。

- **Windows 10 ポータル サイトの新しいガイド機能**   
  Windows 10 用のポータル サイト アプリでは、特定されていないデバイスや登録されていないデバイス向けのガイド付き Intune チュートリアルを利用できます。 新しい機能では、Azure Active Directory の登録 (条件付きアクセス機能に必要) と MDM の登録 (デバイス管理機能に必要) をユーザーに紹介する手順を表示します。 このガイド付きの機能は、ポータル サイトのホーム ページからアクセス可能になります。 ユーザーは、これらの登録を完了していない場合でも、引き続きアプリを使用できますが、機能が制限されます。

  この更新プログラムは、Windows 10 Anniversary Update (ビルド 1607) 以上を実行しているデバイスに表示されます。 これらの変更は、[アプリ UI の新機能](https://docs.microsoft.com/intune/whats-new-app-ui)ページで確認できます。

- **IOS 用ポータル サイト アプリでアプリのタイルの機能強化**  
  ポータル サイトで設定したブランドの色を反映するように、ホームページ上のアプリのタイルのデザインを更新しました。 詳細については、[アプリ UI の新機能](https://docs.microsoft.com/intune/whats-new-app-ui)を参照してください。

- **IOS 用ポータル サイト アプリでアカウントの選択機能を使用できるようになりました**  
  iOS デバイスのユーザーは、職場または学校アカウントを使って他の Microsoft アプリにサインインしている場合、ポータル サイトにサインインするときに、新しいアカウント選択機能が表示されることがあります。 詳細については、[アプリ UI の新機能](https://docs.microsoft.com/intune/whats-new-app-ui)を参照してください。

### <a name="new-in-configuration-manager-technical-preview-1706"></a>Configuration Manager Technical Preview 1706 の新機能

- **新しい Windows 構成アイテムの設定**      
  新しい Windows 構成アイテムは、パスワード、デバイス、ストア、および Microsoft Edge の設定のカテゴリで使用できます。 詳細については、「[New Windows configuration item settings](/sccm/core/get-started/capabilities-in-technical-preview-1706#new-windows-configuration-item-settings)」(新しい Windows 構成アイテム) を参照してください。
  <!-- 1354715 -->

- **新しいデバイス コンプライアンス ポリシー ルール**   
  以前は Intune スタンドアロンにのみ使用可能だったコンプライアンス ポリシー用の新しいオプションを構成できるようになりました。 詳細については、「[デバイス コンプライアンス ポリシーの改善](/sccm/core/get-started/capabilities-in-technical-preview-1706#new-device-compliance-policy-rules)」を参照してください。

- **Android および iOS の登録制限**       
  管理者は、ユーザーが、ハイブリッド環境で個人の Android または iOS デバイスを登録できないことを指定できるようになりました。 このアクションにより、宣言済みのデバイス、会社が所有しているデバイス、またはデバイス登録プログラムで登録されている iOS デバイスに登録されるデバイスを制限することができます。 詳細については、「[Android および iOS の登録制限](/sccm/core/get-started/capabilities-in-technical-preview-1706#android-and-ios-enrollment-restrictions)」を参照してください。
  <!-- 1290826 -->

- **Entrust 証明機関のサポート**      
  Configuration Manager は Entrust 証明機関をサポートするようになりました。 このサポートにより、Microsoft Intune に登録されたデバイスに PFX 証明書を発行できます。    
  <!-- 1350740 -->

  Configuration Manager で証明書登録ポイントの役割を追加するときに、証明機関として Entrust を構成できます。 PFX 証明書を発行する新しい証明書プロファイルを追加する場合は、Microsoft または Entrust のいずれかの証明機関を選択できます。

  **既知の問題**: 1706 Technical Preview では、PFX 証明書は、Microsoft 証明機関用に発行されません。 この問題は、インポートされた PFX 証明書または SCEP プロファイルには影響ありません。

- **macOS VPN プロファイルの Cisco (IPsec) のサポート**      
  接続タイプとして Cisco (IPsec) を指定して macOS VPN プロファイルを作成できます。 詳細については、「[VPN プロファイルの作成](/sccm/mdm/deploy-use/create-vpn-profiles#create-vpn-profiles)」を参照してください。
  <!-- 1321367 -->


## <a name="notices"></a>通知

### <a name="plan-for-change-intune-moving-to-support-ios-10-and-later-in-september-2018"></a>変更の計画: Intune の iOS 10 以降のサポートへの移行 (2018 年 9 月) 
<!--2454656-->

2018 年 9 月には、Apple が iOS 12 をリリースする予定です。 リリースのすぐ後に、Intune の登録、ポータル サイト、Managed Browser は iOS 10 以降のサポートに移行します。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響

Office 365 モバイル アプリは iOS 10 以降でサポートされています。このため、ユーザーは OS やデバイスを既にアップグレードしている場合があります。 その場合、この変更は影響を及ぼしません。

ただし、次に一覧表示するデバイスのいずれかを所有している場合、または登録する場合は、iOS 9 以前しかサポートされないことに注意してください。 引き続き Intune ポータル サイトにアクセスするには、9 月までに、これらのデバイスを iOS 10 以降をサポートするデバイスにアップグレードする必要があります。 

- iPhone 4S
- iPod Touch 
- iPad 2
- iPad (第 3 世代)
- iPad Mini (第 1 世代)

7 月以降、iOS 9 とポータル サイトを 使用している MDM 登録デバイスには、OS やデバイスをアップグレードするよう求めるメッセージが表示されます。 アプリ保護ポリシーを使用する場合は、"iOS オペレーティング システムの最小要件" (警告のみ) アクセス設定を設定することもできます。  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備

組織内で影響を受けるデバイスまたはユーザーを確認します。 Azure Portal の Intune で、**[デバイス]** > **[すべてのデバイス]** に移動し、**[OS]** でフィルター処理します。  **[列]** をクリックして、OS バージョンなどの詳細が目立つようにします。 ユーザーに対して、9 月以前に各自のデバイスをサポートされる OS バージョンにアップグレードするよう要求します。


### <a name="plan-for-change-intune-moving-to-tls-12"></a>変更の計画: Intune の TLS 1.2 への移行

Intune は、クラス最高の暗号化を提供し、サービスが既定で安全であることを保証し、Microsoft Office 365 などの他の Microsoft サービスと連携するために、2018 年 10 月 31 日以降、トランスポート層セキュリティ (TLS) プロトコル バージョン 1.2 をサポートします。 Office は MC128929 でこの変更を伝えています。

#### <a name="how-does-this-affect-me"></a>ユーザーへの影響

2018 年 10 月 31 日時点で、Intune は TLS プロトコル バージョン 1.0 や 1.1 をサポートしなくなります。 すべてのクライアント/サーバーおよびブラウザー/サーバーの組み合わせで TLS バージョン 1.2 を使用して、Intune への正常な接続を保証する必要があります。 この変更は、Intune でサポートされなくなったが Intune 経由で引き続きポリシーを受け取っているエンド ユーザーのデバイス、および TLS バージョン 1.2 を使用できないエンド ユーザーのデバイスに影響を及ぼすことに注意してください。 これには、Android 4.3 以前を実行しているデバイスなどが含まれます。 影響を受けるデバイスとブラウザーの一覧については、以下の追加情報をご覧ください。

2018 年 10 月 31 日以降に古い TLS バージョンの使用に関連する問題が生じる場合は、解決の一環として、TLS 1.2 または TLS 1.2 をサポートしているデバイスに更新する必要があります。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>この変更に対して必要な準備

事前に環境での TLS 1.0 と 1.1 の依存関係を削除し、可能な限りオペレーティング システムのレベルで TLS 1.0 と 1.1 を無効にすることをお勧めします。 TLS 1.2 への移行の計画をすぐに始めてください。 現在 Intune でサポートされていないが引き続きポリシーを受信する可能性があるデバイスの一覧、および TLS バージョン 1.2 を使用して通信することができなくなるデバイスの一覧については、以下のサポート ブログ記事を確認してください。 会社のリソースにアクセスできなくなることを、これらのエンド ユーザーに通知する必要がある場合があります。

詳細については、「[Intune moving to TLS 1.2 for encryption](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/)」(暗号化のための Intune の TLS 1.2 への移行) をご覧ください。


### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode"></a>維持モードに移行中の Windows 8.1 および Windows Phone 8.1 用ポータル サイト 
<!--1428681-->
*2017 年 10 月 6 日*   
 
2017 年 10 月以降、Windows 8.1 および Windows Phone 8.1 用ポータル サイト アプリは維持モードに移行されます。 このモードは、アプリや既存のシナリオ (登録やコンプライアンスなど) で、引き続きこれらのプラットフォームがサポートされることを意味します。 これらのアプリは引き続き、Microsoft Store などの既存のリリース チャネルからダウンロードできます。 

維持モードに移行すると、これらのアプリには重要なセキュリティ更新プログラムのみが適用されるようになります。 追加の更新プログラムや追加機能はリリースされなくなります。 新機能が必要な場合は、デバイスを Windows 10 または Windows 10 Mobile に更新することをおすすめします。 

### <a name="end-of-support-for-ios-80"></a>iOS 8.0 のサポートの終了 
<!---1164477---> iOS のマネージド アプリとポータル サイト アプリから会社のリソースにアクセスするには、iOS 9.0 以降が必要になりました。 9 月以前に更新されていないデバイスは、ポータル サイトまたはそのアプリにアクセスできなくなります。 

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>プラットフォーム サポートのお知らせ: Windows Phone 8.1 のメインストリーム サポートが 2017 年 7 月 11 日に終了
<!-- 1327781 -->
*2017 年 7 月 11 日*

Windows Phone 8.1 プラットフォームのメインストリーム サポートは終了しました。 Windows 8.1 PC のサポートに影響はありません。

Intune サービスによって管理されている Windows Phone 8.1 デバイス (ハイブリッド MDM に登録されているデバイスも含む) への直接的な影響はありません。 登録されたデバイスは引き続き動作します。 すべてのポリシー、構成、アプリが、期待どおりに動作し続けます。 Intune サービス内の Windows Phone 8.1 プラットフォーム、および Windows Phone 8.1 ポータル サイト アプリを対象とした機能強化はないことに注意してください。

できるだけ早い段階で、対象の Windows Phone 8.1 デバイスを Windows 10 Mobile にアップグレードすることをお勧めします。  

### <a name="end-of-support-for-android-43-and-lower"></a>Android 4.3 以前のサポートの終了
<!---1171127--->
*2017 年 7 月 6 日*

Android の管理対象アプリとポータル サイト アプリから会社のリソースにアクセスするには、Android 4.4 以降が必要になりました。 10 月 1 日以前に更新されていないデバイスは、ポータル サイトまたはそのアプリにアクセスできなくなります。 登録されたすべてのデバイスが 12 月までにインベントリから強制的に削除されるため、結果的に会社のリソースにアクセスできなくなります。 MDM なしのアプリ保護ポリシーを使用している場合、アプリは更新プログラムを受信せず、時間の経過と共にアプリのエクスペリエンスの質が低下します。



## <a name="see-also"></a>関連項目

- [過去のハイブリッド MDM 機能と通知](whats-new-hybrid-archive.md)
- [System Center 2012 Configuration Manager の MDM 向け新機能](https://technet.microsoft.com/library/mt445560.aspx)
