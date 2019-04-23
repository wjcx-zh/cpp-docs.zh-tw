---
title: CCustomCommand (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
- ccustomcommand
- customrs.h
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
ms.openlocfilehash: b10d7bccae6fa9b86d072b8e13791f23516b2c63
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028557"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand (CustomRS.H)

`CCustomCommand`類別是提供者命令物件的實作。 它提供的實作`IAccessor`， `ICommandText`，和`ICommandProperties`介面。 `IAccessor`介面是一個資料列集相同。 命令物件會使用存取子，指定的參數繫結。 資料列集物件會使用它們來指定輸出資料行的繫結。 `ICommandText`介面是實用的方式，指定的命令文字。 這個範例會使用`ICommandText`稍後介面，它會新增自訂程式碼時，它也會覆寫`ICommand::Execute`方法。 `ICommandProperties`介面會處理所有的命令和資料列集物件的屬性。

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

`IAccessor`介面管理用於命令和資料列集的所有繫結。 取用者可以呼叫`IAccessor::CreateAccessor`陣列的`DBBINDING`結構。 每個`DBBINDING`結構包含的資料行繫結應該如何處理 （例如型別和長度） 的相關資訊。 提供者會接收此結構，並接著會判斷應該傳送資料的方式，以及是否需要任何轉換。 `IAccessor`介面處理命令中的任何參數時，會在命令物件。

命令物件也會提供實作`IColumnsInfo`。 OLE DB 需要`IColumnsInfo`介面。 介面可讓取用者來擷取命令的參數的相關資訊。 資料列集物件會使用`IColumnsInfo`介面，以傳回給提供者的輸出資料行的相關資訊。

提供者也包含名為介面`IObjectWithSite`。 `IObjectWithSite`介面已實作的 ATL 2.0，以及可讓實作者將本身相關的資訊傳遞給它的子系。 命令物件會使用`IObjectWithSite`資訊向任何產生的建立者是誰的相關資料列集物件。

## <a name="see-also"></a>另請參閱

[提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)