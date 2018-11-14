---
title: OLE DB 提供者樣板架構
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
ms.openlocfilehash: 6256328caa11d188f3a50445f62df096b6f6acb3
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2018
ms.locfileid: "51557033"
---
# <a name="ole-db-provider-template-architecture"></a>OLE DB 提供者樣板架構

## <a name="data-sources-and-sessions"></a>資料來源和工作階段

OLE DB 提供者架構包含資料來源物件和一或多個工作階段。 資料來源物件是每個提供者必須具現化初始物件。 當取用者應用程式需要資料時，它同時會建立啟動提供者的資料來源物件。 資料來源物件會建立工作階段物件 (使用`IDBCreateSession`介面) 透過這取用者會連接到資料來源物件。 ODBC 程式設計人員可以將資料來源物件視為相當於`HENV`和 工作階段物件，相當於`HDBC`。

![提供者架構](../../data/oledb/media/vc4twb1.gif "vc4twb1")

與所建立的來源檔案一起**OLE DB 提供者精靈**，OLE DB 範本實作的資料來源物件。 工作階段是一個物件，對應至 OLE DB `TSession`。

## <a name="mandatory-and-optional-interfaces"></a>必要和選用的介面

OLE DB 提供者範本可讓您預先封裝實作所有必要的介面。 必要和選用的介面是由 OLE DB 定義的數種類型的物件：

- [資料來源](../../data/oledb/data-source-object-interfaces.md)

- [工作階段](../../data/oledb/session-object-interfaces.md)

- [Rowset](../../data/oledb/rowset-object-interfaces.md)

- [命令](../../data/oledb/command-object-interfaces.md)

- [異動](../../data/oledb/transaction-object-interfaces.md)

OLE DB 提供者範本不會實作資料列和儲存體物件。

下表列出必要和選用的介面，如上面所列的物件根據[OLE DB 2.6 SDK 文件](https://docs.microsoft.com/previous-versions/windows/desktop/ms722784(v=vs.85))。

|元件|介面|註解|
|---------------|---------------|-------------|
|[資料來源](../../data/oledb/data-source-object-interfaces.md)([CDataSource](../../data/oledb/cdatasource-class.md))|[必要] `IDBCreateSession`<br /><br /> [必要] `IDBInitialize`<br /><br /> [必要] `IDBProperties`<br /><br /> [必要] `IPersist`<br /><br /> [選用] `IConnectionPointContainer`<br /><br /> [選用] `IDBAsynchStatus`<br /><br /> [選用] `IDBDataSourceAdmin`<br /><br /> [選用] `IDBInfo`<br /><br /> [選用] `IPersistFile`<br /><br /> [選用] `ISupportErrorInfo`|提供者從取用者連線。 物件用來連接，例如使用者識別碼、 密碼和資料來源的名稱上指定屬性。 物件也可用來管理資料來源 （建立、 更新、 刪除、 表格等等）。|
|[工作階段](../../data/oledb/session-object-interfaces.md)([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md))|[必要] `IGetDataSource`<br /><br /> [必要] `IOpenRowset`<br /><br /> [必要] `ISessionProperties`<br /><br /> [選用] `IAlterIndex`<br /><br /> [選用] `IAlterTable`<br /><br /> [選用] `IBindResource`<br /><br /> [選用] `ICreateRow`<br /><br /> [選用] `IDBCreateCommand`<br /><br /> [選用] `IDBSchemaRowset`<br /><br /> [選用] `IIndexDefinition`<br /><br /> [選用] `ISupportErrorInfo`<br /><br /> [選用] `ITableCreation`<br /><br /> [選用] `ITableDefinition`<br /><br /> [選用] `ITableDefinitionWithConstraints`<br /><br /> [選用] `ITransaction`<br /><br /> [選用] `ITransactionJoin`<br /><br /> [選用] `ITransactionLocal`<br /><br /> [選用] `ITransactionObject`|工作階段物件是消費者和提供者之間的單一交談。 類似於 ODBC `HSTMT` ，可以有許多的同時工作階段作用中。<br /><br /> 工作階段物件是主要的連結以前往 OLE DB 功能。 若要取得命令、 交易或資料列集物件，您會瀏覽工作階段物件。|
|[資料列集](../../data/oledb/rowset-object-interfaces.md)([CRowset](../../data/oledb/crowset-class.md))|[必要] `IAccessor`<br /><br /> [必要] `IColumnsInfo`<br /><br /> [必要] `IConvertType`<br /><br /> [必要] `IRowset`<br /><br /> [必要] `IRowsetInfo`<br /><br /> [選用] `IChapteredRowset`<br /><br /> [選用] `IColumnsInfo2`<br /><br /> [選用] `IColumnsRowset`<br /><br /> [選用] `IConnectionPointContainer`<br /><br /> [選用] `IDBAsynchStatus`<br /><br /> [選用] `IGetRow`<br /><br /> [選用] `IRowsetChange`<br /><br /> [選用] `IRowsetChapterMember`<br /><br /> [選用] `IRowsetCurrentIndex`<br /><br /> [選用] `IRowsetFind`<br /><br /> [選用] `IRowsetIdentity`<br /><br /> [選用] `IRowsetIndex`<br /><br /> [選用] `IRowsetLocate`<br /><br /> [選用] `IRowsetRefresh`<br /><br /> [選用] `IRowsetScroll`<br /><br /> [選用] `IRowsetUpdate`<br /><br /> [選用] `IRowsetView`<br /><br /> [選用] `ISupportErrorInfo`<br /><br /> [選用] `IRowsetBookmark`|資料列集物件是從資料來源的資料。 物件用於資料和任何的基本作業 （更新、 fetch、 移動及其他項目） 的資料繫結。 您一定保留和操作資料的資料列集物件。|
|[命令](../../data/oledb/command-object-interfaces.md)([CCommand](ccommand-class.md))|[必要] `IAccessor`<br /><br /> [必要] `IColumnsInfo`<br /><br /> [必要] `ICommand`<br /><br /> [必要] `ICommandProperties`<br /><br /> [必要] `ICommandText`<br /><br /> [必要] `IConvertType`<br /><br /> [選用] `IColumnsRowset`<br /><br /> [選用] `ICommandPersist`<br /><br /> [選用] `ICommandPrepare`<br /><br /> [選用] `ICommandWithParameters`<br /><br /> [選用] `ISupportErrorInfo`<br /><br /> [選用] `ICommandStream`|命令物件會處理資料，例如查詢作業。 它可以處理參數化或非參數化陳述式。<br /><br /> 命令物件也會負責處理參數和輸出資料行的繫結的。 繫結是結構，其中包含擷取的資料行，在資料列集的方式的相關資訊。 它包含例如序數、 資料類型、 長度和狀態資訊。|
|[交易](../../data/oledb/transaction-object-interfaces.md)（選擇性）|[必要] `IConnectionPointContainer`<br /><br /> [必要] `ITransaction`<br /><br /> [選用] `ISupportErrorInfo`|交易物件的資料來源上定義不可部分完成的工作單位，並判斷這些工作單位如何互相關聯性。 此物件不直接支援 OLE DB 提供者範本 （也就是您建立自己的物件）。|

如需詳細資訊，請參閱下列主題：

- [屬性對應](../../data/oledb/property-maps.md)

- [使用者記錄](../../data/oledb/user-record.md)

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 介面](https://docs.microsoft.com/previous-versions/windows/desktop/ms709709(v=vs.85))<br/>
