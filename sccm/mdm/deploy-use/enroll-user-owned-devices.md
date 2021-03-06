---
title: ハイブリッド展開用にユーザー所有のデバイスを登録する
titleSuffix: Configuration Manager
description: Configuration Manager を使用してハイブリッド展開用にユーザー所有のデバイスを登録するさまざまな方法について説明します。
ms.date: 09/08/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 2bdaa8a7-6a64-4b0e-b617-309dcd912c45
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 198e5b65b85e10a1aa64f06361f1ba425e156662
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32345728"
---
# <a name="enroll-user-owned-devices-for-hybrid-deployments-with-configuration-manager"></a>Configuration Manager を使用してハイブリッド展開用にユーザー所有のデバイスを登録する

*適用対象: System Center Configuration Manager (Current Branch)*

ユーザー所有のデバイスは、"bring your own devices"、略して "BYOD" と呼ばれるプロセスで登録を行うことで管理対象にすることができます。 これを行うには、ユーザーがポータル サイト アプリをインストールしてデバイス (iOS、macOS、Android) にサインインするか、職場または学校アカウントをデバイスに追加してドメイン (Windows) に参加します。 このプロセスによりデバイスが Intune に登録され、ユーザーが Intune で管理されるリソースにアクセスできるようになり、Intune が PIN の要求などの特定のデバイス設定を管理できるようになります。

デバイスを管理対象にするには、管理者として最初に[モバイル デバイス管理を設定](setup-hybrid-mdm.md)し、[登録を有効にします](enable-platform-enrollment.md)。 登録を有効にすると、ユーザーは自分のデバイスを登録できます。 ユーザーと共有する考慮事項と手順については、「[Microsoft Intune に関してエンド ユーザーを教育する方法](https://docs.microsoft.com/intune/end-user-educate)」を参照してください。

デバイスを購入する会社または学校は、[会社所有のデバイスの管理](enroll-company-owned-devices.md)を可能にするプログラムを利用できます。
