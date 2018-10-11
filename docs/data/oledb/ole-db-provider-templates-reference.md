---
title: OLE DB 提供者範本參考 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ede88e44c957ae34e9bb9c3f451e0f058310346
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083550"
---
# <a name="ole-db-provider-templates-reference"></a>OLE DB 提供者樣板參考

可以分成下列類別分組的類別和介面的 OLE DB 提供者樣板。 參考資料也包含下列資訊[OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)。  
  
類別會使用下列命名慣例： 名為使用模式的類別`IWidgetImpl`會提供介面的實作`IWidget`。  
  
## <a name="session-classes"></a>工作階段類別  

[IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
從資料來源物件建立新的工作階段，並傳回新建立的工作階段上的要求的介面。 在 資料來源物件上的強制介面。  
  
[ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
藉由呼叫靜態屬性集對應所定義的函式，會實作工作階段屬性。 在您的工作階段類別，應該指定屬性集對應。 在 工作階段上的強制介面。  
  
## <a name="rowset-classes"></a>資料列集類別  

[CRowsetImpl](../../data/oledb/crowsetimpl-class.md)  
  
提供標準的 OLE DB 資料列集實作，而不需要的許多實作介面的多重繼承。 唯一的方法，您必須提供實作`Execute`。  
  
[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
提供的預設實作，用於資料列控制代碼，用於`IRowsetImpl`類別。 資料列控制代碼在邏輯上的結果資料列的唯一標籤。 `IRowsetImpl` 建立新`CSimpleRow`中的每個資料列要求`IRowsetImpl::GetNextRows`。  
  
[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB 會要求實作的提供者`HACCESSOR`，這是標記的陣列`DBBINDING`結構。 提供`HACCESSOR`位址的`BindType`結構。 在 資料列集和命令的必要項。  
  
[IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
提供者的資料行對應所定義的靜態函式的委派。 資料列集和指令的強制介面。  
  
[IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)<br/>
命令或上一個資料列集，請提供可用性資訊的類型轉換。 命令、 資料列集，以及索引資料列集的必要項。 實作`IConvertType`是委派給 OLE DB 所提供的轉換物件的介面。  
  
[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
Implements`IDBSchemaRowset`介面和範本化的建立者函式`CreateSchemaRowset`。  
  
[IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)<br/>
隨即開啟，並傳回包含單一基底資料表或索引中的所有資料列的資料列集。 工作階段物件的強制介面。  
  
[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)<br/>
實作 OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790)介面，讓更新的現有資料列，刪除資料列，並插入新資料列中的資料行的值。  
  
[IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
這個類別繼承自[IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite) ，並覆寫[IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite)。 `IRowsetCreatorImpl` 執行相同的功能`IObjectWithSite`但也可讓 OLE DB 屬性`DBPROPCANSCROLLBACKWARDS`和`DBPROPCANFETCHBACKWARDS`。  
  
[IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)<br/>
實作`IRowsetIdentity`介面，可讓您比較是否兩個資料列的資料或不完全相同。  
  
[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)<br/>
提供實作`IRowset`介面，這是基底的資料列集介面。  
  
[IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)<br/>
實作資料列集屬性，方法是使用內容設定您的命令類別中定義的對應。 在 資料列集上的強制介面。  
  
[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)<br/>
實作 OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190)介面，它會從資料列集提取任意的資料列。 若要支援 OLE DB 的書籤中的資料列集，請繼承自這個類別的資料列集。  
  
[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
實作廣播通知接聽程式連接點上的函式`IID_IRowsetNotify`的資料列集的內容變更。 處理通知的取用者實作[IRowsetNotify](/previous-versions/windows/desktop/ms712959)並註冊該連接點上。  
  
[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
實作 OLE DB [IRowsetUpdate](/previous-versions/windows/desktop/ms714401)介面，讓消費者可以延遲的具有所做的變更傳輸[IRowsetChange](/previous-versions/windows/desktop/ms715790)到資料來源，並復原變更，才能加以傳送。  
  
## <a name="command-classes"></a>命令類別  

[ICommandImpl](../../data/oledb/icommandimpl-class.md)<br/>
提供 `ICommand` 介面的實作。 此介面不可見，但是由`ICommandTextImpl`。 Command 物件上的強制介面。  
  
[ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
這個實作`ICommandProperties`所定義的靜態函式提供介面`BEGIN_PROPSET_MAP`巨集。 在命令中的必要項。  
  
[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
設定、 儲存及傳回命令文字。 在命令中的必要項。  
  
[IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
從工作階段物件建立新的命令，並傳回要求的介面上新建立的命令。 在 工作階段物件上的選擇性介面。  
  
其他命令類別會`IColumnsInfoImpl`和`IAccessorImpl`，前面的資料列集類別 」 一節中所述。  
  
## <a name="data-source-classes"></a>資料來源類別  

[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)<br/>
建立和刪除取用者的連線。 在 資料來源物件和選擇性的介面，列舉值的強制介面。  
  
[IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties` 資料來源物件的強制介面和列舉值的選用介面。 不過，如果列舉程式會公開`IDBInitialize`，它必須公開`IDBProperties`（資料來源上的屬性）。  
  
[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)<br/>
取得資料來源物件介面指標。 在工作階段上的強制介面。  
  
## <a name="other-classes"></a>其他類別  

[CUtlProps](../../data/oledb/cutlprops-class.md)<br/>
會實作各種不同的 OLE DB 屬性的介面屬性 (例如`IDBProperties`， `ISessionProperties`，和`IRowsetInfo`)。  
  
[IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)  
  
實作 OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112)介面、 加入記錄和記錄擷取的資料成員。  
  
## <a name="see-also"></a>另請參閱  

[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[OLE DB 範本](../../data/oledb/ole-db-templates.md)