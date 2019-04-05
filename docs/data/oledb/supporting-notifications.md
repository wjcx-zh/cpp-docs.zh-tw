---
title: 支援告知
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
ms.openlocfilehash: 52c4313de5017b97a193be1afebc020c9896fe6a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035646"
---
# <a name="supporting-notifications"></a>支援告知

## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>實作連接點介面上的提供者和取用者

若要實作通知，提供者類別必須繼承自[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)並[IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md)。

`IRowsetNotifyCP` 實作連接點介面的提供者站台[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))。 `IRowsetNotifyCP` 實作廣播通知接聽程式連接點上的函式`IID_IRowsetNotify`的資料列集的內容變更。

您也必須實作並註冊`IRowsetNotify`在取用者 （也稱為接收） 使用[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) ，好讓取用者可以處理通知。 在取用者實作連接點介面的詳細資訊，請參閱[接收通知](../../data/oledb/receiving-notifications.md)。

此外，此類別必須有對應定義的連接點項目，像這樣：

```cpp
BEGIN_CONNECTION_POINT_MAP
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)
END_CONNECTION_POINT_MAP
```

## <a name="adding-irowsetnotify"></a>新增 IRowsetNotify

若要新增`IRowsetNotify`，您需要新增`IConnectionPointContainerImpl<rowset-name>`和`IRowsetNotifyCP<rowset-name>`繼承鏈結。

例如，以下是的繼承鏈結`RUpdateRowset`中[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV):

> [!NOTE]
> 範例程式碼可能會與不同功能為此處所列;您應該將範例程式碼做為較新版本。

```cpp
///////////////////////////////////////////////////////////////////////////
// class RUpdateRowset (in rowset.h)

class RUpdateRowset :
public CRowsetImpl< RUpdateRowset, CAgentMan, CUpdateCommand,
         CAtlArray< CAgentMan, CAtlArray<CAgentMan>>, CSimpleRow,
         IRowsetScrollImpl< RUpdateRowset, IRowsetScroll >>,
      public IRowsetUpdateImpl< RUpdateRowset, CAgentMan >,
      public IConnectionPointContainerImpl<RUpdateRowset>,
      public IRowsetNotifyCP<RUpdateRowset>
```

### <a name="setting-com-map-entries"></a>設定 COM 對應項目

您也需要將下列內容新增至您的資料列集中的 COM 對應：

```cpp
COM_INTERFACE_ENTRY(IConnectionPointContainer)
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)
```

這些巨集可以讓任何人呼叫`QueryInterface`為您的連接點容器 (的基礎`IRowsetNotify`) 來尋找您的提供者上要求的介面。 如需如何使用連接點的範例，請參閱 ATL 多邊形的範例和教學課程。

### <a name="setting-connection-point-map-entries"></a>設定連接點對應項目

您也需要新增一個連接點對應。 它應該看起來像：

```cpp
BEGIN_CONNECTION_POINT_MAP(rowset-name)
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))
END_CONNECTION_POINT_MAP()
```

這個連接點對應可讓元件，尋求`IRowsetNotify`介面，以在您的提供者中找到它。

### <a name="setting-properties"></a>設定屬性

您也需要將下列屬性新增至您的提供者。 您只需要新增您所支援的介面為基礎的屬性。

|屬性|新增 如果您支援|
|--------------|------------------------|
|DBPROP_IConnectionPointContainer|永遠|
|DBPROP_NOTIFICATIONGRANULARITY|永遠|
|DBPROP_NOTIFICATIONPHASES|永遠|
|DBPROP_NOTIFYCOLUMNSET|`IRowsetChange`|
|DBPROP_NOTIFYROWDELETE|`IRowsetChange`|
|DBPROP_NOTIFYROWINSERT|`IRowsetChange`|
|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|永遠|
|DBPROP_NOTIFYROWFIRSTCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWSETRELEASE|永遠|
|DBPROP_NOTIFYROWUNDOCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDODELETE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDOINSERT|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUPDATE|`IRowsetUpdate`|

通知的實作大多已內嵌在 OLE DB 提供者樣板。 如果您未新增`IRowsetNotifyCP`到您的繼承鏈結，編譯器會移除所有程式碼從編譯資料流，因而讓您的程式碼大小較小。

## <a name="see-also"></a>另請參閱

[進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)