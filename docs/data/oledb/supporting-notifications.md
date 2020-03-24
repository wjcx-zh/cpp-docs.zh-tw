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
ms.openlocfilehash: d29f84a0a5b33d55c0a04a4c758050cf9746f72a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209537"
---
# <a name="supporting-notifications"></a>支援告知

## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>在提供者和取用者上執行連接點介面

若要執行通知，提供者類別必須繼承自[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)和[IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md)。

`IRowsetNotifyCP` 會為連接點介面[IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85))實作為提供者網站。 `IRowsetNotifyCP` 會執行廣播函式，以建議連接點上的接聽程式 `IID_IRowsetNotify` 資料列集內容的變更。

您也必須使用[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) ，在取用者（也稱為接收器）上執行並註冊 `IRowsetNotify`，讓取用者可以處理通知。 如需在取用者上執行連接點介面的詳細資訊，請參閱[接收通知](../../data/oledb/receiving-notifications.md)。

此外，類別必須有定義連接點專案的對應，如下所示：

```cpp
BEGIN_CONNECTION_POINT_MAP
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)
END_CONNECTION_POINT_MAP
```

## <a name="adding-irowsetnotify"></a>加入 IRowsetNotify

若要新增 `IRowsetNotify`，您需要將 `IConnectionPointContainerImpl<rowset-name>` 和 `IRowsetNotifyCP<rowset-name>` 新增至您的繼承鏈。

例如，以下是[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)中 `RUpdateRowset` 的繼承鏈：

> [!NOTE]
> 範例程式碼可能會與此處所列的不同；您應該將範例程式碼視為更新版本。

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

### <a name="setting-com-map-entries"></a>設定 COM 對應專案

您也需要將下列內容加入至資料列集中的 COM 對應：

```cpp
COM_INTERFACE_ENTRY(IConnectionPointContainer)
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)
```

這些宏可讓任何人針對您的連接點容器（`IRowsetNotify`的基礎）呼叫 `QueryInterface`，以在您的提供者上尋找所要求的介面。 如需如何使用連接點的範例，請參閱 ATL 多邊形範例和教學課程。

### <a name="setting-connection-point-map-entries"></a>設定連接點對應專案

您也需要新增連接點對應。 它看起來應該像這樣：

```cpp
BEGIN_CONNECTION_POINT_MAP(rowset-name)
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))
END_CONNECTION_POINT_MAP()
```

這個連接點對應可讓元件尋找 `IRowsetNotify` 介面，以便在您的提供者中尋找。

### <a name="setting-properties"></a>設定屬性

您也需要將下列屬性新增至您的提供者。 您只需要根據支援的介面來新增屬性。

|屬性|如果您支援，請新增|
|--------------|------------------------|
|DBPROP_IConnectionPointContainer|一律|
|DBPROP_NOTIFICATIONGRANULARITY|一律|
|DBPROP_NOTIFICATIONPHASES|一律|
|DBPROP_NOTIFYCOLUMNSET|`IRowsetChange`|
|DBPROP_NOTIFYROWDELETE|`IRowsetChange`|
|DBPROP_NOTIFYROWINSERT|`IRowsetChange`|
|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|一律|
|DBPROP_NOTIFYROWFIRSTCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWSETRELEASE|一律|
|DBPROP_NOTIFYROWUNDOCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDODELETE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDOINSERT|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUPDATE|`IRowsetUpdate`|

通知的大部分執行已內嵌于 OLE DB 提供者範本中。 如果您未將 `IRowsetNotifyCP` 加入至繼承鏈，編譯器會從您的編譯資料流程移除所有該程式碼，因此會使您的程式碼大小變小。

## <a name="see-also"></a>另請參閱

[進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)
