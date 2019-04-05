---
title: OLE DB 消費者樣板參考
ms.date: 11/04/2016
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc.templates.ole
- vc-attr.db_source
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
ms.openlocfilehash: fb0b24798b3f2682bbbec7624df34b40a2a9f4cc
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032267"
---
# <a name="ole-db-consumer-templates-reference"></a>OLE DB 消費者樣板參考

OLE DB 消費者樣板包含下列類別。 上的參考資料也包含的主題[OLE DB 消費者樣板的巨集](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)。

## <a name="session-classes"></a>工作階段類別

[CDataConnection](../../data/oledb/cdataconnection-class.md)<br/>
管理與資料來源的連線。 這是工作的有用的類別，來建立用戶端，因為它會封裝所需的物件 （資料來源和工作階段） 和一些您需要連接到資料來源時所執行。

[CDataSource](../../data/oledb/cdatasource-class.md)<br/>
對應至 OLE DB 資料來源物件，表示透過提供者連接到資料來源。 一或多個資料庫工作階段，皆由`CSession`物件，可能需要在單一連接上的位置。

[CEnumerator](../../data/oledb/cenumerator-class.md)<br/>
對應至 OLE DB 列舉值物件，擷取可用的資料來源的資料列集資訊。

[CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)<br/>
使用`CEnumerator`從列舉值的資料列集存取資料。 此資料列集是由資料來源並顯示從目前的列舉值的列舉值所組成。

[CSession](../../data/oledb/csession-class.md)<br/>
表示單一的資料庫存取工作階段。 一或多個工作階段可以與每個相關聯`CDataSource`物件。

## <a name="accessor-classes"></a>存取子類別

[CAccessor](../../data/oledb/caccessor-class.md)<br/>
用於以靜態方式繫結至資料來源的記錄。 當您知道資料來源的結構時，請使用這個存取子類別。

[CAccessorBase](../../data/oledb/caccessorbase-class.md)<br/>
所有存取子類別的基底類別。

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
存取子可建立在執行階段，根據資料列集的資料行資訊。 使用此類別來擷取資料，如果您不知道資料來源的結構。

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
命令類型未知時，可以使用存取子。 取得參數資訊，藉由呼叫`ICommandWithParameters`介面，如果提供者支援介面。

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
可讓您存取資料來源，就不需要知道資料庫的基礎結構。

[CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
類似於`CDynamicStringAccessor`不同之處在於此類別會要求存取資料存放區做為 ANSI 字串資料的資料。

[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
類似於`CDynamicStringAccessor`不同之處在於此類別會要求存取資料存放區做為 UNICODE 字串資料的資料。

[CManualAccessor](../../data/oledb/cmanualaccessor-class.md)<br/>
存取子方法來處理資料行和命令參數。 使用這個類別中，您可以使用任何資料類型，只要提供者可以將類型轉換。

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
可用來當做樣板引數時您不想要支援的參數或輸出資料行的類別。

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)<br/>
類似於`CDynamicStringAccessor`不同之處在於此類別會將從資料存放區，做為 XML 格式 （標記） 的資料存取的所有資料的都轉換。

## <a name="rowset-classes"></a>資料列集類別

[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)<br/>
封裝資料列集和其相關聯的存取子。

[CArrayRowset](../../data/oledb/carrayrowset-class.md)<br/>
用來存取的資料列集使用陣列語法項目。

[CBulkRowset](../../data/oledb/cbulkrowset-class.md)<br/>
用來擷取和管理大量的資料列擷取透過單一呼叫的多個資料列控制代碼。

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
可用來當做樣板引數如果命令未傳回資料列集。

[cRestrictions](../../data/oledb/crestrictions-class.md)<br/>
用來指定結構描述資料列的限制。

[CRowset](../../data/oledb/crowset-class.md)<br/>
用來操作、 設定及擷取資料列集資料。

[CStreamRowset](../../data/oledb/cstreamrowset-class.md)<br/>
傳回`ISequentialStream`而不是資料列集物件，然後使用`Read`方法來擷取 XML 格式的資料。 （SQL Server 2000 已採取的格式，請注意這項功能只能搭配 SQL Server 2000）。

[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)<br/>
提供的虛擬實作`IRowsetNotify`，使用空白的函式`IRowsetNotify`方法`OnFieldChange`， `OnRowChange`，和`OnRowsetChange`。

[結構描述資料列集類別和 Typedef 類別](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)

OLE DB 樣板為您提供一組對應至 OLE DB 結構描述資料列集的類別。

## <a name="command-classes"></a>命令類別

[CCommand](../../data/oledb/ccommand-class.md)<br/>
用來設定和執行參數為基礎的 OLE DB 命令。 若要只開啟一個簡單的資料列集，請使用`CTable`改。

[CMultipleResults](../../data/oledb/cmultipleresults-class.md)<br/>
做為範本引數`CCommand`範本，當您想要處理多個結果集的命令。

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
做為樣板引數的樣板類別，例如`CCommand`和`CTable`，採用的存取子類別引數。 使用`CNoAccessor`如果您不想要支援的參數或輸出資料行的類別。

[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)<br/>
做為範本引數`CCommand`範本，當您想要處理單一資料列集的命令。 `CNoMultipleResults` 是範本引數的預設值。

[CNoRowset](../../data/oledb/cnorowset-class.md)<br/>
做為範本引數`CCommand`或`CTable`如果命令或資料表不會傳回一個資料列集。

[CTable](../../data/oledb/ctable-class.md)<br/>
用來存取不含任何參數的簡單資料列集。

## <a name="property-classes"></a>屬性類別

[CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)<br/>
用來傳遞這取用者需要屬性資訊的屬性識別碼的陣列。 屬性會屬於一個屬性集。

[CDBPropSet](../../data/oledb/cdbpropset-class.md)<br/>
用來設定提供者的屬性。

## <a name="bookmark-class"></a>書籤類別

[CBookmark](../../data/oledb/cbookmark-class.md)<br/>
用做為索引來存取資料列集中的資料。

## <a name="error-class"></a>錯誤類別

[CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)<br/>
用來擷取 OLE DB 錯誤資訊。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者樣板參考](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 樣板](../../data/oledb/ole-db-templates.md)