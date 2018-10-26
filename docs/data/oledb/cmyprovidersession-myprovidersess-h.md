---
title: CCustomSession (CustomSess.H) |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyprovidersession
- myprovidersess.h
- ccustomsession
- customsess.h
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
- CCustomSession class in CustomSess.H
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8873247ee54884236ed3472c345fb15b99e97131
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076681"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession (CustomSess.H)

*自訂*Sess.H 包含宣告和實作的 OLE DB 工作階段物件。 資料來源物件會建立工作階段物件，表示消費者和提供者之間的交談。 數個同時工作階段可以有一個資料來源開啟。 繼承清單`CCustomSession`遵循：

```cpp
/////////////////////////////////////////////////////////////////////////
// CCustomSession
class ATL_NO_VTABLE CCustomSession :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IGetDataSourceImpl<CCustomSession>,
   public IOpenRowsetImpl<CCustomSession>,
   public ISessionPropertiesImpl<CCustomSession>,
   public IObjectWithSiteSessionImpl<CCustomSession>,
   public IDBSchemaRowsetImpl<CCustomSession>,
   public IDBCreateCommandImpl<CCustomSession, CCustomCommand>
```

工作階段物件會繼承`IGetDataSource`， `IOpenRowset`， `ISessionProperties`，和`IDBCreateCommand`。 `IGetDataSource`介面允許工作階段擷取資料來源建立它。 這是您需要從您所建立的資料來源或資料來源可以提供其他資訊取得內容時相當實用。 `ISessionProperties`介面會處理工作階段的所有屬性。 `IOpenRowset`和`IDBCreateCommand`介面用來執行資料庫作業。 如果提供者支援的命令，它會實作`IDBCreateCommand`介面。 它用來建立可執行命令的命令物件。 提供者一律會實作`IOpenRowset`物件。 它用來產生簡單的資料列集提供者。 它是預設的資料列集 (比方說， `"select * from mytable"`) 提供者。

精靈也會產生工作階段的三個類別： `CCustomSessionColSchema`， `CCustomSessionPTSchema`，和`CCustomSessionTRSchema`。 這些工作階段會使用結構描述資料列。 結構描述資料列讓提供者傳回給取用者的中繼資料，而不需要執行查詢或提取資料的取用者。 擷取中繼資料會遠比探索提供者功能更快。

OLE DB 規格所要求的提供者實作`IDBSchemaRowset`介面支援三個結構描述資料列集型別： DBSCHEMA_COLUMNS、 DBSCHEMA_PROVIDER_TYPES 和 DBSCHEMA_TABLES。 精靈會產生每個結構描述資料列集的實作。 每個精靈所產生的類別包含`Execute`方法。 在此`Execute`方法中，您可以傳回資料給提供者所支援相關的資料表、 資料行和資料類型。 這項資料通常是在編譯時期已知的。

## <a name="see-also"></a>另請參閱

[提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)