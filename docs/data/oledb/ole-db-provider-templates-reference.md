---
title: OLE DB 提供者樣板參考
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
ms.openlocfilehash: 567d4131229ee25d0d69ff4456398e05af387f0e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210037"
---
# <a name="ole-db-provider-templates-reference"></a>OLE DB 提供者樣板參考

OLE DB 提供者範本的類別和介面可以分組為下列分類。 參考資料也包含[OLE DB 提供者範本之宏](../../data/oledb/macros-for-ole-db-provider-templates.md)的相關資訊。

類別會使用下列命名慣例：一個名為且模式為 `IWidgetImpl` 的類別會提供介面的執行 `IWidget`。

## <a name="session-classes"></a>會話類別

[IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
從資料來源物件建立新的會話，並在新建立的會話上傳回要求的介面。 資料來源物件上的強制介面。

[ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
藉由呼叫屬性集對應所定義的靜態函式，來實作用會話屬性。 您應該在會話類別中指定屬性集對應。 會話上的強制介面。

## <a name="rowset-classes"></a>資料列集類別

[CRowsetImpl](../../data/oledb/crowsetimpl-class.md)

提供標準的 OLE DB 資料列集執行，而不需要多個實作為介面的繼承。 唯一必須提供實作為 `Execute`的方法。

[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
提供資料列控制碼的預設實作為，用於 `IRowsetImpl` 類別中。 資料列控制碼在邏輯上是結果資料列的唯一標記。 `IRowsetImpl` 會針對 `IRowsetImpl::GetNextRows`中要求的每個資料列建立新的 `CSimpleRow`。

[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB 需要提供者來執行 `HACCESSOR`，這是 `DBBINDING` 結構陣列的標記。 提供 `HACCESSOR`，其為 `BindType` 結構的位址。 在資料列集和命令上是必要的。

[IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
委派給提供者資料行對應所定義的靜態函式。 資料列集和命令的強制介面。

[IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)<br/>
提供命令或資料列集上類型轉換可用性的資訊。 在命令、資料列集和索引資料列集上是必要的。 藉由委派給 OLE DB 所提供的轉換物件，來執行 `IConvertType` 介面。

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
執行 `IDBSchemaRowset` 介面和範本化 creator 函數 `CreateSchemaRowset`。

[IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)<br/>
開啟並傳回資料列集，其中包含單一基表或索引的所有資料列。 會話物件的強制介面。

[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)<br/>
會執行 OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))介面，這可讓您更新現有資料列中的資料行值、刪除資料列，以及插入新的資料列。

[IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
這個類別繼承自[IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) ，並覆寫[IObjectWithSite：： SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)。 `IRowsetCreatorImpl` 會執行與 `IObjectWithSite` 相同的功能，但也會啟用 `DBPROPCANSCROLLBACKWARDS` 和 `DBPROPCANFETCHBACKWARDS`OLE DB 屬性。

[IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)<br/>
會執行 `IRowsetIdentity` 介面，這可讓您比較兩個數據列是否相同。

[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)<br/>
提供 `IRowset` 介面的執行，也就是基底資料列集介面。

[IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)<br/>
使用在命令類別中定義的屬性集對應，來執行資料列集屬性。 資料列集上的強制介面。

[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)<br/>
會執行 OLE DB 的[IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))介面，它會從資料列集中提取任意資料列。 若要支援資料列集中 OLE DB 書簽，請將資料列集繼承自這個類別。

[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
會執行廣播函式，以建議連接點上的接聽程式 `IID_IRowsetNotify` 資料列集內容的變更。 處理通知的取用者會執行[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) ，並在該連接點上註冊。

[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
會執行 OLE DB [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))介面，讓取用者延遲將[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))所做的變更傳輸至資料來源，並在傳輸前復原變更。

## <a name="command-classes"></a>命令類別

[ICommandImpl](../../data/oledb/icommandimpl-class.md)<br/>
提供 `ICommand` 介面的實作。 此介面不可見，但會由 `ICommandTextImpl`處理。 命令物件上的強制介面。

[ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
這個 `ICommandProperties` 介面的執行是由 `BEGIN_PROPSET_MAP` 宏所定義的靜態函式所提供。 命令上的必要。

[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
設定、儲存和傳回命令文字。 命令上的必要。

[IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
從會話物件建立新的命令，並在新建立的命令上傳回要求的介面。 會話物件上的選擇性介面。

其他命令類別是 `IColumnsInfoImpl` 和 `IAccessorImpl`，如上方的資料列集類別一節中所述。

## <a name="data-source-classes"></a>資料來源類別

[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)<br/>
建立和刪除取用者的連接。 資料來源物件上的強制介面和枚舉器上的選擇性介面。

[IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties` 是資料來源物件的強制介面，以及枚舉器的選擇性介面。 不過，如果列舉值公開 `IDBInitialize`，它必須公開 `IDBProperties` （資料來源上的屬性）。

[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)<br/>
取得資料來源物件的介面指標。 會話上的強制介面。

## <a name="other-classes"></a>其他類別

[CUtlProps](../../data/oledb/cutlprops-class.md)<br/>
會針對各種 OLE DB 屬性介面（例如 `IDBProperties`、`ISessionProperties`和 `IRowsetInfo`）來執行屬性。

[IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)

會執行 OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85))介面、在資料成員中加入記錄，以及從中抓取記錄。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[OLE DB 範本](../../data/oledb/ole-db-templates.md)
