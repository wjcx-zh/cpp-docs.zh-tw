---
title: OLE DB 提供者樣板架構
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
ms.openlocfilehash: 89e07f95853c3611b7cceaef3f247c220c630add
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509552"
---
# <a name="ole-db-provider-template-architecture"></a>OLE DB 提供者樣板架構

## <a name="data-sources-and-sessions"></a>資料來源和工作階段

OLE DB 提供者架構包含一個資料來源物件和一個或多個會話。 資料來源物件是每個提供者都必須具現化的初始物件。 當取用者應用程式需要資料時，它會共同建立資料來源物件以啟動提供者。 資料來源物件會使用介面) 來建立會話物件 (，取用 `IDBCreateSession` 者會透過此介面連接到資料來源物件。 ODBC 程式設計人員可以將資料來源物件視為與相同 `HENV` ，並將會話物件視為相當於 `HDBC` 。

![提供者架構](../../data/oledb/media/vc4twb1.gif "提供者架構")

連同 **OLE DB Provider Wizard**所建立的原始程式檔，OLE DB 範本會執行資料來源物件。 會話是對應至 OLE DB 的物件 `TSession` 。

## <a name="mandatory-and-optional-interfaces"></a>必要和選用介面

OLE DB 提供者範本為所有必要的介面提供預先封裝的實作為。 必要和選用的介面是由數個物件類型的 OLE DB 所定義：

- [資料來源](../../data/oledb/data-source-object-interfaces.md)

- [工作階段](../../data/oledb/session-object-interfaces.md)

- [資料列集](../../data/oledb/rowset-object-interfaces.md)

- [命令](../../data/oledb/command-object-interfaces.md)

- [交易](../../data/oledb/transaction-object-interfaces.md)

OLE DB 提供者範本不會執行資料列和儲存物件。

下表根據 [OLE DB 2.6 SDK 檔](/previous-versions/windows/desktop/ms722784(v=vs.85))，列出上面所列物件的必要和選用介面。

|元件|介面|註解|
|---------------|---------------|-------------|
|[資料來源](../../data/oledb/data-source-object-interfaces.md) ([CDataSource](../../data/oledb/cdatasource-class.md)) |不必 `IDBCreateSession`<br /><br /> 不必 `IDBInitialize`<br /><br /> 不必 `IDBProperties`<br /><br /> 不必 `IPersist`<br /><br /> 參數 `IConnectionPointContainer`<br /><br /> 參數 `IDBAsynchStatus`<br /><br /> 參數 `IDBDataSourceAdmin`<br /><br /> 參數 `IDBInfo`<br /><br /> 參數 `IPersistFile`<br /><br /> 參數 `ISupportErrorInfo`|從取用者到提供者的連接。 物件是用來指定連接上的屬性，例如使用者識別碼、密碼和資料來源名稱。 物件也可以用來管理資料來源 (建立、更新、刪除、資料表等) 。|
|[Session](../../data/oledb/session-object-interfaces.md) ([CSession](./cdataconnection-class.md#op_csession_amp)) |不必 `IGetDataSource`<br /><br /> 不必 `IOpenRowset`<br /><br /> 不必 `ISessionProperties`<br /><br /> 參數 `IAlterIndex`<br /><br /> 參數 `IAlterTable`<br /><br /> 參數 `IBindResource`<br /><br /> 參數 `ICreateRow`<br /><br /> 參數 `IDBCreateCommand`<br /><br /> 參數 `IDBSchemaRowset`<br /><br /> 參數 `IIndexDefinition`<br /><br /> 參數 `ISupportErrorInfo`<br /><br /> 參數 `ITableCreation`<br /><br /> 參數 `ITableDefinition`<br /><br /> 參數 `ITableDefinitionWithConstraints`<br /><br /> 參數 `ITransaction`<br /><br /> 參數 `ITransactionJoin`<br /><br /> 參數 `ITransactionLocal`<br /><br /> 參數 `ITransactionObject`|會話物件是取用者與提供者之間的單一交談。 它類似于 ODBC `HSTMT` ，因為可能會有許多同時可用的會話。<br /><br /> 會話物件是取得 OLE DB 功能的主要連結。 若要取得命令、交易或資料列集物件，請流覽會話物件。|
|資料列[集](../../data/oledb/rowset-object-interfaces.md) ([CRowset](../../data/oledb/crowset-class.md)) |不必 `IAccessor`<br /><br /> 不必 `IColumnsInfo`<br /><br /> 不必 `IConvertType`<br /><br /> 不必 `IRowset`<br /><br /> 不必 `IRowsetInfo`<br /><br /> 參數 `IChapteredRowset`<br /><br /> 參數 `IColumnsInfo2`<br /><br /> 參數 `IColumnsRowset`<br /><br /> 參數 `IConnectionPointContainer`<br /><br /> 參數 `IDBAsynchStatus`<br /><br /> 參數 `IGetRow`<br /><br /> 參數 `IRowsetChange`<br /><br /> 參數 `IRowsetChapterMember`<br /><br /> 參數 `IRowsetCurrentIndex`<br /><br /> 參數 `IRowsetFind`<br /><br /> 參數 `IRowsetIdentity`<br /><br /> 參數 `IRowsetIndex`<br /><br /> 參數 `IRowsetLocate`<br /><br /> 參數 `IRowsetRefresh`<br /><br /> 參數 `IRowsetScroll`<br /><br /> 參數 `IRowsetUpdate`<br /><br /> 參數 `IRowsetView`<br /><br /> 參數 `ISupportErrorInfo`<br /><br /> 參數 `IRowsetBookmark`|資料列集物件是資料來源中的資料。 此物件是用於該資料的系結，以及任何基本作業 (更新、提取、移動和其他) 資料。 您永遠都有資料列集物件，可保留及運算元據。|
|[命令](../../data/oledb/command-object-interfaces.md) ([CCommand](ccommand-class.md)) |不必 `IAccessor`<br /><br /> 不必 `IColumnsInfo`<br /><br /> 不必 `ICommand`<br /><br /> 不必 `ICommandProperties`<br /><br /> 不必 `ICommandText`<br /><br /> 不必 `IConvertType`<br /><br /> 參數 `IColumnsRowset`<br /><br /> 參數 `ICommandPersist`<br /><br /> 參數 `ICommandPrepare`<br /><br /> 參數 `ICommandWithParameters`<br /><br /> 參數 `ISupportErrorInfo`<br /><br /> 參數 `ICommandStream`|命令物件會處理資料（例如查詢）的作業。 它可以處理參數化或非參數化的語句。<br /><br /> Command 物件也負責處理參數和輸出資料行的系結。 系結是一種結構，其中包含有關如何取出資料列集內資料行的資訊。 它包含序數、資料類型、長度和狀態等資訊。|
|[交易](../../data/oledb/transaction-object-interfaces.md) (選擇性) |不必 `IConnectionPointContainer`<br /><br /> 不必 `ITransaction`<br /><br /> 參數 `ISupportErrorInfo`|交易對象會在資料來源上定義不可部分完成的工作單位，並決定這些工作單位彼此之間的關聯性。 OLE DB 提供者範本不直接支援這個物件 (也就是說，您會) 建立自己的物件。|

如需詳細資訊，請參閱下列主題：

- [屬性對應](../../data/oledb/property-maps.md)

- [使用者記錄](../../data/oledb/user-record.md)

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 介面](/previous-versions/windows/desktop/ms709709(v=vs.85))<br/>
