---
title: ATL 模組類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e067b1d72b80950b4ed33fbae8cac7333ac0438
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083070"
---
# <a name="atl-module-classes"></a>ATL 模組類別

本主題討論的是新 ATL 7.0 中的模組類別。

## <a name="ccommodule-replacement-classes"></a>CComModule 取代類別

舊版的 ATL 用`CComModule`。 ATL 7.0 中`CComModule`功能會取代數個類別：

- [CAtlBaseModule](../atl/reference/catlbasemodule-class.md)包含使用 ATL 的大部分應用程式所需的資訊 包含的 HINSTANCE 的模組和資源執行個體。

- [CAtlComModule](../atl/reference/catlcommodule-class.md)包含 ATL 中的 COM 類別所需的資訊

- [CAtlWinModule](../atl/reference/catlwinmodule-class.md)包含所需的 ATL 中的視窗類別資訊

- [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md)包含支援偵錯介面。

- [CAtlModule](../atl/reference/catlmodule-class.md)下列`CAtlModule`-衍生的類別會自訂為包含在特定應用程式類型的資訊。 這些類別中的大部分成員都可以覆寫：

   - [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) DLL 應用程式中使用。 提供標準的匯出程式碼。

   - [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) EXE 應用程式中使用。 提供程式碼所需要的是 EXE。

   - [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md)提供支援，以建立 Windows NT 和 Windows 2000 服務。

`CComModule` 是仍然可供回溯相容性。

## <a name="reasons-for-distributing-ccommodule-functionality"></a>散發 CComModule 功能的原因

功能`CComModule`已散發到數個新的類別，原因如下：

- 進行中的功能`CComModule`細微。

   適用於 COM、 視窗化、 偵錯介面，和應用程式專屬 （DLL 或 EXE） 功能的支援現在為個別的類別。

- 自動宣告每個模組的全域執行的個體。

   要求的模組類別的全域執行個體連結至專案。

- 移除需要呼叫 Init 和詞彙的方法。

   Init 和詞彙的方法已移至建構函式和解構函式模組類別;此外已不再需要呼叫 Init 和詞彙。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[類別概觀](../atl/atl-class-overview.md)

