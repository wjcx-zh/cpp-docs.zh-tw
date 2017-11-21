---
title: "OLE DB 提供者樣板架構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB [C++], object model
- architecture [C++], OLE DB Provider
- OLE DB provider templates, object model
ms.assetid: 639304a3-f9e0-44dc-8d0c-0ebd2455b363
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 289d1d5f09f60b829c6dd7d1f1b00c0de3562518
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ole-db-provider-template-architecture"></a>OLE DB 提供者樣板架構
## <a name="data-sources-and-sessions"></a>資料來源和工作階段  
 OLE DB 提供者架構包含資料來源物件和一或多個工作階段。 資料來源物件是每個提供者必須具現化的初始物件。 當取用者應用程式需要的資料時，同時會建立啟動提供者資料來源物件。 資料來源物件會建立工作階段物件 (使用**IDBCreateSession**介面) 透過其取用者會連接到資料來源物件。 ODBC 程式設計人員可以將資料來源物件視為相當於**HENV**和工作階段物件，相當於**HDBC**。  
  
 ![提供者架構](../../data/oledb/media/vc4twb1.gif "vc4twb1")  
  
 OLE DB 提供者精靈 所建立的來源檔案，以及 OLE DB 樣板會實作資料來源物件。 工作階段是對應至 OLE DB 物件**TSession**。  
  
## <a name="mandatory-and-optional-interfaces"></a>必要和選擇性介面  
 OLE DB 提供者範本可讓您預先封裝實作所有必要的介面。 必要和選擇性介面的定義方式 OLE DB for 幾種類型的物件：  
  
-   [資料來源](../../data/oledb/data-source-object-interfaces.md)  
  
-   [工作階段](../../data/oledb/session-object-interfaces.md)  
  
-   [資料列集](../../data/oledb/rowset-object-interfaces.md)  
  
-   [命令](../../data/oledb/command-object-interfaces.md)  
  
-   [異動](../../data/oledb/transaction-object-interfaces.md)  
  
 請注意，OLE DB 提供者範本不會實作資料列和儲存體物件。  
  
 下表列出強制和選擇性的介面，如上面所列的物件根據[OLE DB 2.6 SDK 文件](https://msdn.microsoft.com/en-us/library/ms722784.aspx)。  
  
|元件|介面|註解|  
|---------------|---------------|-------------|  
|[資料來源](../../data/oledb/data-source-object-interfaces.md)([CDataSource](../../data/oledb/cdatasource-class.md))|[必要]**IDBCreateSession**<br /><br /> [必要]**IDBInitialize**<br /><br /> [必要]`IDBProperties`<br /><br /> [必要]`IPersist`<br /><br /> [選用]**IConnectionPointContainer**<br /><br /> [選用]**IDBAsynchStatus**<br /><br /> [選用]**IDBDataSourceAdmin**<br /><br /> [選用]**IDBInfo**<br /><br /> [選用]`IPersistFile`<br /><br /> [選用]**ISupportErrorInfo**|提供者從取用者連接。 物件用來連接，例如使用者識別碼、 密碼和資料來源的名稱上指定屬性。 物件也可用來管理資料來源 （建立、 更新、 刪除、 表格和等等）。|  
|[工作階段](../../data/oledb/session-object-interfaces.md)([CSession](../../data/oledb/cdataconnection-operator-csession-amp.md))|[必要]**IGetDataSource**<br /><br /> [必要]`IOpenRowset`<br /><br /> [必要]**ISessionProperties**<br /><br /> [選用]**IAlterIndex**<br /><br /> [選用]**IAlterTable**<br /><br /> [選用]**IBindResource**<br /><br /> [選用]**ICreateRow**<br /><br /> [選用]**IDBCreateCommand**<br /><br /> [選用]**IDBSchemaRowset**<br /><br /> [選用]**IIndexDefinition**<br /><br /> [選用]**ISupportErrorInfo**<br /><br /> [選用]**ITableCreation**<br /><br /> [選用]**ITableDefinition**<br /><br /> [選用]**ITableDefinitionWithConstraints**<br /><br /> [選用]**Itransaction::**<br /><br /> [選用]**ITransactionJoin**<br /><br /> [選用]**ITransactionLocal**<br /><br /> [選用]**j**|工作階段物件代表消費者和提供者之間的單一交談。 有點類似於 ODBC **HSTMT** ，可以有許多的工作階段使用中。<br /><br /> 工作階段物件是主要的連結，以取得 OLE DB 功能。 若要取得命令、 交易或資料列集物件，您瀏覽工作階段物件。|  
|[資料列集](../../data/oledb/rowset-object-interfaces.md)([CRowset](../../data/oledb/crowset-class.md))|[必要]`IAccessor`<br /><br /> [必要]`IColumnsInfo`<br /><br /> [必要]**IConvertType**<br /><br /> [必要]`IRowset`<br /><br /> [必要]`IRowsetInfo`<br /><br /> [選用]**IChapteredRowset**<br /><br /> [選用]**IColumnsInfo2**<br /><br /> [選用]**IColumnsRowset**<br /><br /> [選用]**IConnectionPointContainer**<br /><br /> [選用]**IDBAsynchStatus**<br /><br /> [選用]**IGetRow**<br /><br /> [選用]`IRowsetChange`<br /><br /> [選用]**IRowsetChapterMember**<br /><br /> [選用]**IRowsetCurrentIndex**<br /><br /> [選用]**IRowsetFind**<br /><br /> [選用]**IRowsetIdentity**<br /><br /> [選用]**IRowsetIndex**<br /><br /> [選用]`IRowsetLocate`<br /><br /> [選用]**IRowsetRefresh**<br /><br /> [選用]`IRowsetScroll`<br /><br /> [選用]`IRowsetUpdate`<br /><br /> [選用]**IRowsetView**<br /><br /> [選用]**ISupportErrorInfo**<br /><br /> [選用]**IRowsetBookmark**|資料列集物件表示從資料來源的資料。 此物件負責該資料和任何的基本作業 （更新、 fetch、 移動，以及其他） 的資料繫結。 此外，您都有包含，以及操作資料的資料列集物件。|  
|[命令](../../data/oledb/command-object-interfaces.md)([CCommand](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409))|[必要]`IAccessor`<br /><br /> [必要]`IColumnsInfo`<br /><br /> [必要]`ICommand`<br /><br /> [必要]**ICommandProperties**<br /><br /> [必要]`ICommandText`<br /><br /> [必要]**IConvertType**<br /><br /> [選用]**IColumnsRowset**<br /><br /> [選用]**ICommandPersist**<br /><br /> [選用]**m**<br /><br /> [選用]`ICommandWithParameters`<br /><br /> [選用]**ISupportErrorInfo**<br /><br /> [選用]**ICommandStream**|命令物件會處理資料，例如查詢作業。 它可以處理參數化或非參數化陳述式。<br /><br /> 命令物件也會負責處理參數和輸出資料行的繫結。 繫結是結構，其中包含擷取的資料行，在資料列集的方式的相關資訊。 它包含例如序數、 資料類型、 長度和狀態資訊。|  
|[交易](../../data/oledb/transaction-object-interfaces.md)（選擇性）|[必要]**IConnectionPointContainer**<br /><br /> [必要]**Itransaction::**<br /><br /> [選用]**ISupportErrorInfo**|交易物件上的資料來源定義不可部分完成的工作單位，並判斷這些工作單位如何彼此相關。 此物件不直接支援 OLE DB 提供者樣板 （也就是您建立自己的物件）。|  
  
 如需詳細資訊，請參閱下列主題：  
  
-   [屬性對應](../../data/oledb/property-maps.md)  
  
-   [使用者資料錄](../../data/oledb/user-record.md)  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 介面](https://msdn.microsoft.com/en-us/library/ms709709.aspx)