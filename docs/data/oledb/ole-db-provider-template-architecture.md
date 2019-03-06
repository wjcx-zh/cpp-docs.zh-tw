---
title: OLE DB 提供者樣板架構
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
ms.openlocfilehash: b6d177d793451b7c5e9c19f6d40add973a627d60
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422997"
---
# <a name="ole-db-provider-template-architecture"></a>OLE DB 提供者樣板架構

## <a name="data-sources-and-sessions"></a>資料來源和工作階段

OLE DB 提供者架構包含資料來源物件和一或多個工作階段。 資料來源物件是每個提供者必須具現化初始物件。 當取用者應用程式需要資料時，它同時會建立啟動提供者的資料來源物件。 資料來源物件會建立工作階段物件 (使用`IDBCreateSession`介面) 透過這取用者會連接到資料來源物件。 ODBC 程式設計人員可以將資料來源物件視為相當於`HENV`和 工作階段物件，相當於`HDBC`。

![提供者架構](../../data/oledb/media/vc4twb1.gif "提供者架構")

與所建立的來源檔案一起**OLE DB 提供者精靈**，OLE DB 範本實作的資料來源物件。 工作階段是一個物件，對應至 OLE DB `TSession`。

## <a name="mandatory-and-optional-interfaces"></a>必要和選用的介面

OLE DB 提供者範本可讓您預先封裝實作所有必要的介面。 必要和選用的介面是由 OLE DB 定義的數種類型的物件：

- [資料來源](../../data/oledb/data-source-object-interfaces.md)

- [工作階段](../../data/oledb/session-object-interfaces.md)

- [Rowset](../../data/oledb/rowset-object-interfaces.md)

- [命令](../../data/oledb/command-object-interfaces.md)

- [異動](../../data/oledb/transaction-object-interfaces.md)

OLE DB 提供者範本不會實作資料列和儲存體物件。

下表列出必要和選用的介面，如上面所列的物件根據[OLE DB 2.6 SDK 文件](/previous-versions/windows/desktop/ms722784(v=vs.85))。

|元件|介面|註解|
|---------------|---------------|-------------|
|[資料來源](../../data/oledb/data-source-object-interfaces.md)([CDataSource](../../data/oledb/cdatasource-class.md))|[mandatory] `IDBCreateSession`<br /><br /> [mandatory] `IDBInitialize`<br /><br /> [mandatory] `IDBProperties`<br /><br /> [mandatory] `IPersist`<br /><br /> [optional] `IConnectionPointContainer`<br /><br /> [optional] `IDBAsynchStatus`<br /><br /> [optional] `IDBDataSourceAdmin`<br /><br /> [optional] `IDBInfo`<br /><br /> [optional] `IPersistFile`<br /><br /> [optional] `ISupportErrorInfo`|提供者從取用者連線。 物件用來連接，例如使用者識別碼、 密碼和資料來源的名稱上指定屬性。 物件也可用來管理資料來源 （建立、 更新、 刪除、 表格等等）。|
|[工作階段](../../data/oledb/session-object-interfaces.md)([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md))|[mandatory] `IGetDataSource`<br /><br /> [mandatory] `IOpenRowset`<br /><br /> [mandatory] `ISessionProperties`<br /><br /> [optional] `IAlterIndex`<br /><br /> [optional] `IAlterTable`<br /><br /> [optional] `IBindResource`<br /><br /> [optional] `ICreateRow`<br /><br /> [optional] `IDBCreateCommand`<br /><br /> [optional] `IDBSchemaRowset`<br /><br /> [optional] `IIndexDefinition`<br /><br /> [optional] `ISupportErrorInfo`<br /><br /> [optional] `ITableCreation`<br /><br /> [optional] `ITableDefinition`<br /><br /> [optional] `ITableDefinitionWithConstraints`<br /><br /> [optional] `ITransaction`<br /><br /> [optional] `ITransactionJoin`<br /><br /> [optional] `ITransactionLocal`<br /><br /> [optional] `ITransactionObject`|工作階段物件是消費者和提供者之間的單一交談。 類似於 ODBC `HSTMT` ，可以有許多的同時工作階段作用中。<br /><br /> 工作階段物件是主要的連結以前往 OLE DB 功能。 若要取得命令、 交易或資料列集物件，您會瀏覽工作階段物件。|
|[Rowset](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md))|[mandatory] `IAccessor`<br /><br /> [mandatory] `IColumnsInfo`<br /><br /> [mandatory] `IConvertType`<br /><br /> [mandatory] `IRowset`<br /><br /> [mandatory] `IRowsetInfo`<br /><br /> [optional] `IChapteredRowset`<br /><br /> [optional] `IColumnsInfo2`<br /><br /> [optional] `IColumnsRowset`<br /><br /> [optional] `IConnectionPointContainer`<br /><br /> [optional] `IDBAsynchStatus`<br /><br /> [optional] `IGetRow`<br /><br /> [optional] `IRowsetChange`<br /><br /> [optional] `IRowsetChapterMember`<br /><br /> [optional] `IRowsetCurrentIndex`<br /><br /> [optional] `IRowsetFind`<br /><br /> [optional] `IRowsetIdentity`<br /><br /> [optional] `IRowsetIndex`<br /><br /> [optional] `IRowsetLocate`<br /><br /> [optional] `IRowsetRefresh`<br /><br /> [optional] `IRowsetScroll`<br /><br /> [optional] `IRowsetUpdate`<br /><br /> [optional] `IRowsetView`<br /><br /> [optional] `ISupportErrorInfo`<br /><br /> [optional] `IRowsetBookmark`|資料列集物件是從資料來源的資料。 物件用於資料和任何的基本作業 （更新、 fetch、 移動及其他項目） 的資料繫結。 您一定保留和操作資料的資料列集物件。|
|[命令](../../data/oledb/command-object-interfaces.md)([CCommand](ccommand-class.md))|[mandatory] `IAccessor`<br /><br /> [mandatory] `IColumnsInfo`<br /><br /> [mandatory] `ICommand`<br /><br /> [mandatory] `ICommandProperties`<br /><br /> [mandatory] `ICommandText`<br /><br /> [mandatory] `IConvertType`<br /><br /> [optional] `IColumnsRowset`<br /><br /> [optional] `ICommandPersist`<br /><br /> [optional] `ICommandPrepare`<br /><br /> [optional] `ICommandWithParameters`<br /><br /> [optional] `ISupportErrorInfo`<br /><br /> [optional] `ICommandStream`|命令物件會處理資料，例如查詢作業。 它可以處理參數化或非參數化陳述式。<br /><br /> 命令物件也會負責處理參數和輸出資料行的繫結的。 繫結是結構，其中包含擷取的資料行，在資料列集的方式的相關資訊。 它包含例如序數、 資料類型、 長度和狀態資訊。|
|[交易](../../data/oledb/transaction-object-interfaces.md)（選擇性）|[mandatory] `IConnectionPointContainer`<br /><br /> [mandatory] `ITransaction`<br /><br /> [optional] `ISupportErrorInfo`|交易物件的資料來源上定義不可部分完成的工作單位，並判斷這些工作單位如何互相關聯性。 此物件不直接支援 OLE DB 提供者範本 （也就是您建立自己的物件）。|

如需詳細資訊，請參閱下列主題：

- [屬性對應](../../data/oledb/property-maps.md)

- [使用者記錄](../../data/oledb/user-record.md)

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 介面](/previous-versions/windows/desktop/ms709709(v=vs.85))<br/>
