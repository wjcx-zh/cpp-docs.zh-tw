---
title: "OLE DB 提供者樣板參考 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.templates.ole
dev_langs: C++
helpviewer_keywords: OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a68c3f0b161a21749ad49b1b89a1356b757d4b76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ole-db-provider-templates-reference"></a>OLE DB 提供者樣板參考
類別和介面的 OLE DB 提供者樣板可以分為下列類別。 參考資料也包含下列資訊[OLE DB 提供者樣板巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)。  
  
 類別會使用下列命名慣例： 類別的使用模式**IWidgetImpl**會提供介面的實作**IWidget**。  
  
## <a name="session-classes"></a>工作階段類別  
 [IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)  
 從資料來源物件建立新的工作階段，並傳回要求的介面上新建立的工作階段。 資料來源物件上的強制介面。  
  
 [ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)  
 藉由呼叫靜態屬性集對應所定義的函式會實作工作階段屬性。 屬性集對應應該指定在您的工作階段類別。 工作階段的強制介面。  
  
## <a name="rowset-classes"></a>資料列集類別  
 [CRowsetImpl](../../data/oledb/crowsetimpl-class.md)  
  
 提供標準的 OLE DB 資料列集實作，而不需要許多實作介面的多重繼承。 唯一的方法，您必須提供實作**Execute**。  
  
 [CSimpleRow](../../data/oledb/csimplerow-class.md)  
 提供資料列控制代碼，使用中的預設實作`IRowsetImpl`類別。 資料列控制代碼邏輯上是唯一的標記的結果資料列。 `IRowsetImpl`建立新`CSimpleRow`要求中的每個資料列`IRowsetImpl::GetNextRows`。  
  
 [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)  
 OLE DB 需要實作的提供者**HACCESSOR**，即為陣列的標記**DBBINDING**結構。 提供**HACCESSOR**是位址的 s **BindType**結構。 資料列集和命令上的必要項。  
  
 [IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)  
 提供者的資料行對應所定義的靜態函式委派。 資料列集和指令的強制介面。  
  
 [IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)  
 命令或上一個資料列集，請提供可用性資訊的型別轉換。 命令、 資料列集和索引資料列集上的必要項。 實作**IConvertType**委派給 OLE DB 所提供的轉換物件的介面。  
  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)  
 實作**IDBSchemaRowset**介面和範本化的建立者函式`CreateSchemaRowset`。  
  
 [IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)  
 開啟並傳回包含單一基底資料表或索引的所有資料列的資料列集。 工作階段物件的強制介面。  
  
 [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)  
 實作 OLE DB [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)介面，讓更新的現有資料列，刪除資料列，並插入新資料列中的資料行的值。  
  
 [IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)  
 此類別繼承自[IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765)和覆寫[IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869)。 `IRowsetCreatorImpl`執行相同的函式做為`IObjectWithSite`但也可讓 OLE DB 屬性**DBPROPCANSCROLLBACKWARDS**和**DBPROPCANFETCHBACKWARDS**。  
  
 [IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)  
 實作**IRowsetIdentity**介面，可讓您比較是否兩個資料列或不完全相同。  
  
 [IRowsetImpl](../../data/oledb/irowsetimpl-class.md)  
 提供的實作`IRowset`介面，這是基底的資料列集介面。  
  
 [IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)  
 實作資料列集屬性，方法是使用屬性集合命令類別中定義的對應。 資料列集上的強制介面。  
  
 [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)  
 實作 OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx)介面，從資料列集擷取任意資料列。 若要支援 OLE DB 書籤中的資料列集，請從這個類別繼承的資料列集。  
  
 [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)  
 實作廣播函式來通知接聽程式連接點上**IID_IRowsetNotify**的資料列集內容的變更。 處理通知的取用者實作[IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)並註冊該連接點上。  
  
 [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)  
 實作 OLE DB [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx)介面，讓取用者延遲與所做的變更傳輸[IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)到資料來源，並復原變更再傳輸。  
  
## <a name="command-classes"></a>命令類別  
 [ICommandImpl](../../data/oledb/icommandimpl-class.md)  
 提供 `ICommand` 介面的實作。 這個介面不可見，但會處理由**ICommandTextImpl**。 Command 物件上的強制介面。  
  
 [ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)  
 這項實作**ICommandProperties**所定義之靜態函式所提供介面`BEGIN_PROPSET_MAP`巨集。 在命令中的必要項。  
  
 [ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)  
 設定、 儲存，並傳回命令文字。 在命令中的必要項。  
  
 [IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)  
 建立新的命令，從工作階段物件，並傳回要求的介面上新建立的命令。 選擇性的工作階段物件介面。  
  
 其他命令類別會`IColumnsInfoImpl`和`IAccessorImpl`中資料列集類別上面所述。  
  
## <a name="data-source-classes"></a>資料來源類別  
 [IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)  
 建立和刪除與取用者的連接。 在資料來源物件與在列舉值的選擇性介面上的強制介面。  
  
 [IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)  
 `IDBProperties`是資料來源物件的強制介面和列舉值的選用介面。 不過，如果列舉值公開**IDBInitialize**，它必須公開`IDBProperties`（資料來源上的屬性）。  
  
 [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)  
 取得資料來源物件的介面指標。 在工作階段上的強制介面。  
  
## <a name="other-classes"></a>其他類別  
 [CUtlProps](../../data/oledb/cutlprops-class.md)  
 會實作各種不同的 OLE DB 屬性的介面屬性 (例如， `IDBProperties`， **ISessionProperties**，和`IRowsetInfo`)。  
  
 [IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)  
  
 實作 OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx)介面，加入記錄和資料成員從擷取記錄。  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [OLE DB 範本](../../data/oledb/ole-db-templates.md)