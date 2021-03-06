---
title: Mobile Threat Defense
titleSuffix: Configuration Manager
description: Configuration Manager と Intune Mobile Threat Defense パートナーを使用して、デバイス、ネットワーク、アプリケーションのリスクを基に会社のリソースへのアクセスを制限します。
ms.date: 03/02/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 4c0e6824-2dfe-4700-b817-d5631e0eb872
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 6aeed0c7e509ee96b226f5d1c7649bcf84af3af8
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32347605"
---
# <a name="intune-mobile-threat-defense-connectors-in-configuration-manager"></a>Configuration Manager の Intune Mobile Threat Defense コネクター

*適用対象: System Center Configuration Manager (Current Branch)*

[ハイブリッド MDM 展開 (SCCM と Intune)](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management) および Intune と Mobile Threat Defense パートナー間の統合により、デバイス リスク評価に基づき、会社のリソースおよびデータへのアクセスを制御できます。

Intune Mobile Threat Defense コネクターを使用すると、選択した Mobile Threat Defense ベンダーをコンプライアンス ポリシーと条件付きアクセス規則の情報ソースとして活用できます。 これにより、IT 管理者が、特に危険にさらされたモバイル デバイスから、Exchange、Sharepoint などの企業リソースに保護レイヤーを追加することができます。

## <a name="what-problem-does-this-solve"></a>これはどのような問題を解決しますか。

会社は物理的な脅威、アプリ ベースの脅威、ネットワーク ベースの脅威など、新種の脅威やオペレーティング システムの脆弱性から機密データを保護する必要があります。
これまで、企業は PC の防御を積極的に行ってきましたが、モバイル デバイスは監視や保護のない状態が続いていました。 モバイル プラットフォームには、アプリの分離や検証済みコンシューマー アプリ ストアなどの防御手法が組み込まれていますが、依然として高度な攻撃を受けやすい状態にあります。 今日では、仕事でモバイル デバイスを利用して、機密情報にアクセスする社員が増えています。 より高度さを増す攻撃からモバイル デバイスを守る必要があります。

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense コネクターのしくみ

このコネクターは、Intune と選択した Mobile Threat Defense ベンダーの間に通信チャネルを作成することで、会社のリソースを保護します。 Intune Mobile Threat Defense パートナーは、直感的で簡単に展開できるモバイル デバイス向けアプリケーションを提供します。これらのアプリケーションは、脅威情報を積極的にスキャンして分析し、レポートや強制を目的として Intune と共有します。 たとえば、Mobile Threat Defense アプリが、ネットワーク上の電話が Man in the Middle 攻撃に対して脆弱なネットワークに接続されていることを Mobile Threat Defense ベンダーに報告した場合、この情報は共有されて適切なリスク レベル (低/中/高) に分類されます。その後、Intune で構成済みのリスク レベル許容度と比較されて、デバイスが侵害されたときに選択した特定のリソースへのアクセスを無効にする必要があるかどうかが判断されます。

## <a name="sample-scenarios"></a>サンプル事例

Mobile Threat Defense ソリューションによってデバイスが感染したと見なされた場合

![](http://i.imgur.com/Li1WUOU.png)

デバイスが修復されたときにアクセスが許可されます。

![](http://i.imgur.com/VCIwpdz.png)

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense パートナー

デバイス、ネットワーク、アプリケーションのリスクに基づいて、会社のリソースへのアクセスを保護する方法について説明します。次のものを使用します。

- [Lookout](https://docs.microsoft.com/sccm/protect/deploy-use/lookout-mobile-threat-defense-in-configuration-manager)
