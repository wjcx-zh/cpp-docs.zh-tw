---
title: ATL 模組類別
ms.date: 11/04/2016
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
ms.openlocfilehash: 2b72cac0da06b70a40e01fcc75da52f1678f3f64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317378"
---
# <a name="atl-module-classes"></a>ATL 模組類別

本主題討論 ATL 7.0 中新增的模組類。

## <a name="ccommodule-replacement-classes"></a>CCom 模組更換類別

使用的`CComModule`ATL 的早期版本。 在 ATL 7.0`CComModule`中, 功能被幾個類別替換:

- [CAtlBase 模組](../atl/reference/catlbasemodule-class.md)包含大多數使用 ATL 的應用程式所需的資訊。 包含模組和資源實例的 HINSTANCE。

- [CAtlCom 模組](../atl/reference/catlcommodule-class.md)包含 ATL 中的 COM 類所需的資訊。

- [CAtlWin 模組](../atl/reference/catlwinmodule-class.md)包含 ATL 中視窗類所需的資訊。

- [CAtlDebug 介面模組](../atl/reference/catldebuginterfacesmodule-class.md)包含對介面調試的支援。

- [CAtlModule](../atl/reference/catlmodule-class.md)以下`CAtlModule`派生類被自定義以包含特定應用程式類型中所需的資訊。 可以重寫這些類中的大多數成員:

  - [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md)用於 DLL 應用程式。 提供標準導出的代碼。

  - [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md)用於 EXE 應用程式。 提供 EXE 中所需的代碼。

  - [CAtl 服務模組T](../atl/reference/catlservicemodulet-class.md)提供創建 Windows NT 和 Windows 2000 服務的支援。

`CComModule`仍然可用於向後相容性。

## <a name="reasons-for-distributing-ccommodule-functionality"></a>分發 CComModule 功能的原因

由於以下原因`CComModule`,將的功能分發到幾個新類中:

- 使功能以`CComModule`粒度進行。

   現在,對 COM、視窗、介面調試和特定於應用程式的 (DLL 或 EXE) 功能的支持處於單獨的類中。

- 自動聲明每個模組的全域實例。

   所需模組類的全域實例連結到專案中。

- 刪除調用 Init 和術語方法的必要性。

   Init 和術語方法已移入模組類的構造函數和析構函數;不再需要調用 Init 和術語。

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[類別概觀](../atl/atl-class-overview.md)
