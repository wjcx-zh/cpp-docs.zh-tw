---
title: CCustomCommand (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidercommand
- ccustomcommand
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
ms.openlocfilehash: afa8571173117a23962eb84f6fa5b4cf2c3c46e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211753"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

`CCustomCommand` 類別是提供者命令物件的執行。 它提供了 `IAccessor`、`ICommandText`和 `ICommandProperties` 介面的執行。 `IAccessor` 介面與資料列集中的介面相同。 命令物件會使用存取子來指定參數的系結。 資料列集物件會使用它們來指定輸出資料行的系結。 `ICommandText` 介面是一種以原文方式指定命令的實用方法。 這個範例會在稍後新增自訂程式碼時使用 `ICommandText` 介面;它也會覆寫 `ICommand::Execute` 方法。 `ICommandProperties` 介面會處理命令和資料列集物件的所有屬性。

```cpp
// CCustomCommand
class ATL_NO_VTABLE CCustomCommand :
class ATL_NO_VTABLE CCustomCommand :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IAccessorImpl<CCustomCommand>,
   public ICommandTextImpl<CCustomCommand>,
   public ICommandPropertiesImpl<CCustomCommand>,
   public IObjectWithSiteImpl<CCustomCommand>,
   public IConvertTypeImpl<CCustomCommand>,
   public IColumnsInfoImpl<CCustomCommand>
```

`IAccessor` 介面會管理命令和資料列集中所使用的所有系結。 取用者會使用 `DBBINDING` 結構的陣列來呼叫 `IAccessor::CreateAccessor`。 每個 `DBBINDING` 結構都會包含如何處理資料行系結的相關資訊（例如類型和長度）。 提供者會接收結構，然後決定要如何傳送資料，以及是否需要進行任何轉換。 命令物件中會使用 `IAccessor` 介面來處理命令中的任何參數。

Command 物件也提供 `IColumnsInfo`的執行。 OLE DB 需要 `IColumnsInfo` 介面。 介面可讓取用者從命令取得參數的相關資訊。 資料列集物件會使用 `IColumnsInfo` 介面，將輸出資料行的相關資訊傳回給提供者。

提供者也包含稱為 `IObjectWithSite`的介面。 `IObjectWithSite` 介面是在 ATL 2.0 中實作為，可讓實施者將本身的相關資訊傳遞給其子系。 命令物件會使用 `IObjectWithSite` 資訊，告訴任何產生的資料列集物件建立者。

## <a name="see-also"></a>另請參閱

[提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)
