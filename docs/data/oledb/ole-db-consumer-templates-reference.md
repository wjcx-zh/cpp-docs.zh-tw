---
title: OLE DB 消費者樣板參考
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
ms.openlocfilehash: 52fe3df7e872c257aa8802f84c548ad57d21be27
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447403"
---
# <a name="ole-db-consumer-templates-reference"></a>OLE DB 消費者樣板參考

OLE DB 取用者範本包含下列類別。 參考資料也包含[OLE DB 取用者範本之宏](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)的相關主題。

## <a name="session-classes"></a>會話類別

[CDataConnection](../../data/oledb/cdataconnection-class.md)<br/>
管理與資料來源的連接。 這是用來建立用戶端的實用類別，因為它會封裝必要的物件（資料來源和會話），以及連接到資料來源時所需執行的一些工作。

[CDataSource](../../data/oledb/cdatasource-class.md)<br/>
對應至 OLE DB 資料來源物件，代表透過提供者連接至資料來源的連線。 一個或多個資料庫會話（每個都由 `CSession` 物件表示）都可以在單一連接上進行。

[CEnumerator](../../data/oledb/cenumerator-class.md)<br/>
對應至 OLE DB 列舉值物件，它會抓取可用資料來源的資料列集資訊。

[CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)<br/>
由 `CEnumerator` 用來存取列舉值資料列集的資料。 這個資料列集是由目前列舉值所顯示的資料來源和枚舉器所組成。

[CSession](../../data/oledb/csession-class.md)<br/>
表示單一資料庫存取會話。 一或多個會話可以與每個 `CDataSource` 物件相關聯。

## <a name="accessor-classes"></a>存取子類別

[CAccessor](../../data/oledb/caccessor-class.md)<br/>
用於靜態系結至資料來源的記錄。 當您知道資料來源的結構時，請使用此存取子類別。

[CAccessorBase](../../data/oledb/caccessorbase-class.md)<br/>
所有存取子類別的基類。

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
可在執行時間建立的存取子，根據資料列集的資料行資訊。 如果您不知道資料來源的結構，請使用這個類別來取得資料。

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
當命令類型不明時，可以使用的存取子。 如果提供者支援介面，則藉由呼叫 `ICommandWithParameters` 介面來取得參數資訊。

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
當您不知道資料庫的基礎結構時，可讓您存取資料來源。

[CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
類似于 `CDynamicStringAccessor`，不同之處在于這個類別會要求從資料存放區存取的資料做為 ANSI 字串資料。

[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
類似于 `CDynamicStringAccessor`，不同之處在于這個類別會要求從資料存放區存取的資料做為 UNICODE 字串資料。

[CManualAccessor](../../data/oledb/cmanualaccessor-class.md)<br/>
具有方法的存取子，可處理資料行和命令參數。 使用這個類別時，只要提供者可以轉換類型，您就可以使用任何資料類型。

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
當您不想要讓類別支援參數或輸出資料行時，可以使用做為樣板引數。

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)<br/>
類似于 `CDynamicStringAccessor`，不同之處在于這個類別會將從資料存放區存取的所有資料轉換為 XML 格式（已標記）的資料。

## <a name="rowset-classes"></a>資料列集類別

[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)<br/>
封裝資料列集及其相關聯的存取子。

[CArrayRowset](../../data/oledb/carrayrowset-class.md)<br/>
用來存取使用陣列語法之資料列集的元素。

[CBulkRowset](../../data/oledb/cbulkrowset-class.md)<br/>
藉由使用單一呼叫來抓取多個資料列控制碼，用來大量提取和運算元據列。

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
如果命令不會傳回資料列集，就可以使用做為樣板引數。

[CRestrictions](../../data/oledb/crestrictions-class.md)<br/>
用來指定架構資料列集的限制。

[CRowset](../../data/oledb/crowset-class.md)<br/>
用來操作、設定和取出資料列集資料。

[CStreamRowset](../../data/oledb/cstreamrowset-class.md)<br/>
傳回 `ISequentialStream` 物件，而不是資料列集;然後，您可以使用 `Read` 方法來抓取 XML 格式的資料。 （SQL Server 2000 執行格式設定; 請注意，這項功能僅適用于 SQL Server 2000）。

[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)<br/>
提供 `IRowsetNotify`的虛擬執行，其中包含 `IRowsetNotify` 方法 `OnFieldChange`、`OnRowChange`和 `OnRowsetChange`的空白函數。

[結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)

OLE DB 範本會提供一組對應至 OLE DB 架構資料列集的類別。

## <a name="command-classes"></a>命令類別

[CCommand](../../data/oledb/ccommand-class.md)<br/>
用來設定和執行以參數為基礎的 OLE DB 命令。 若只要開啟簡單的資料列集，請改用 `CTable`。

[CMultipleResults](../../data/oledb/cmultipleresults-class.md)<br/>
當您想要命令處理多個結果集時，用來做為 `CCommand` 範本的樣板引數。

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
用來當做樣板類別的樣板引數（例如 `CCommand` 和 `CTable`），該範本會接受存取子類別引數。 如果您不想要讓類別支援參數或輸出資料行，請使用 `CNoAccessor`。

[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)<br/>
當您想要命令處理單一資料列集時，用來做為 `CCommand` 範本的樣板引數。 `CNoMultipleResults` 是範本引數的預設值。

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
做為 `CCommand` 或 `CTable` 的樣板引數（如果命令或資料表不會傳回資料列集）。

[CTable](../../data/oledb/ctable-class.md)<br/>
用來存取沒有參數的簡單資料列集。

## <a name="property-classes"></a>屬性類別

[CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)<br/>
用來傳遞屬性識別碼的陣列，取用者需要屬性資訊。 屬性屬於一個屬性集。

[CDBPropSet](../../data/oledb/cdbpropset-class.md)<br/>
用來設定提供者的屬性。

## <a name="bookmark-class"></a>Bookmark 類別

[CBookmark](../../data/oledb/cbookmark-class.md)<br/>
當做索引，用來存取資料列集中的資料。

## <a name="error-class"></a>Error 類別

[CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)<br/>
用來取出 OLE DB 錯誤資訊。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本參考](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 範本](../../data/oledb/ole-db-templates.md)