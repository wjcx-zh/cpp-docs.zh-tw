---
title: 接收告知
ms.date: 10/24/2018
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
ms.openlocfilehash: 4b630a9728770a5e35e6d6300cf465b90238350c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209770"
---
# <a name="receiving-notifications"></a>接收告知

OLE DB 提供在發生事件時接收通知的介面。 OLE DB 程式設計**人員參考**中的[OLE DB 物件通知](/previous-versions/windows/desktop/ms725406(v=vs.85))會加以描述。 這些事件的設定會使用標準的 COM 連接點機制。 例如，想要透過 `IRowsetNotify` 抓取事件的 ATL 物件會藉由將 `IRowsetNotify` 新增至類別衍生清單，並透過 COM_INTERFACE_ENTRY 宏公開，來執行 `IRowsetNotify` 介面。

`IRowsetNotify` 有三個方法，可以在不同的時間呼叫。 如果您只想要回應其中一種方法，您可以使用[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)類別，它會針對您不感興趣的方法傳回 E_NOTIMPL。

當您建立資料列集時，必須告知提供者您想要傳回的資料列集物件支援 `IConnectionPointContainer`，這是設定通知所需的。

下列程式碼示範如何從 ATL 物件開啟資料列集，並使用 `AtlAdvise` 函數來設定通知接收。 `AtlAdvise` 會傳回當您呼叫 `AtlUnadvise`時所使用的 cookie。

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_IConnectionPointContainer, true);
```

然後，使用下列程式碼：

```cpp
product.Open(session, _T("Products"), &propset);

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);
```

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)
