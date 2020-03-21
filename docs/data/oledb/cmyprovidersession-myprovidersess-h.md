---
title: CCustomSession (CustomSess.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidersession
- myprovidersess.h
- ccustomsession
- customsess.h
helpviewer_keywords:
- CMyProviderSession class in MyProviderSess.H
- OLE DB providers, wizard-generated files
- CCustomSession class in CustomSess.H
ms.assetid: d37ad471-cf05-49c5-aa47-cd10824d777f
ms.openlocfilehash: 4775f21c1e0fa7666d24b4d6a55e099bc6ae55a2
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079763"
---
# <a name="ccustomsession-customsessh"></a>CCustomSession (CustomSess.H)

*自訂*Ses 之始包含 OLE DB 會話物件的宣告和執行。 資料來源物件會建立會話物件，並代表取用者和提供者之間的交談。 可以針對一個資料來源開啟數個同步會話。 `CCustomSession` 的繼承清單如下：

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

Session 物件繼承自 `IGetDataSource`、`IOpenRowset`、`ISessionProperties`和 `IDBCreateCommand`。 `IGetDataSource` 介面允許會話抓取建立它的資料來源。 如果您需要從您建立的資料來源或資料來源可以提供的其他資訊取得屬性，這會很有用。 `ISessionProperties` 介面會處理會話的所有屬性。 `IOpenRowset` 和 `IDBCreateCommand` 介面是用來執行資料庫工作。 如果提供者支援命令，它會執行 `IDBCreateCommand` 介面。 它是用來建立可執行命令的命令物件。 提供者一律會實行 `IOpenRowset` 物件。 它是用來從提供者產生資料列集。 這是來自提供者的預設資料列集（例如 `"select * from mytable"`）。

此 wizard 也會產生三個會話類別： `CCustomSessionColSchema`、`CCustomSessionPTSchema`和 `CCustomSessionTRSchema`。 這些會話會用於架構資料列集。 架構資料列集可讓提供者將中繼資料傳回給取用者，而不需要取用者必須執行查詢或提取資料。 比起尋找提供者的功能，提取中繼資料的速度會快得多。

OLE DB 規格要求執行 `IDBSchemaRowset` 介面的提供者支援三個架構資料列集類型： DBSCHEMA_COLUMNS、DBSCHEMA_PROVIDER_TYPES 和 DBSCHEMA_TABLES。 Wizard 會針對每個架構資料列集產生實作為。 Wizard 所產生的每個類別都包含一個 `Execute` 方法。 在這個 `Execute` 方法中，您可以將資料傳回給提供者，瞭解您支援的資料表、資料行和資料類型。 此資料在編譯時期為已知。

## <a name="see-also"></a>另請參閱

[提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)<br/>
