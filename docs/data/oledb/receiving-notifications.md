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
ms.openlocfilehash: 67f7eb5f77dc68b57f04ab4d016680255cb1ae86
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416016"
---
# <a name="receiving-notifications"></a>接收告知

OLE DB 提供事件發生時接收通知的介面。 這些所述[OLE DB 物件通知](/previous-versions/windows/desktop/ms725406(v=vs.85))中**OLE DB 程式設計人員參考**。 這些事件的安裝程式會使用標準的 COM 連接點機制。 比方說，ATL 物件，想要擷取事件通過`IRowsetNotify`會實作`IRowsetNotify`介面，藉由新增`IRowsetNotify`類別衍生清單並將其公開透過 COM_INTERFACE_ENTRY 巨集。

`IRowsetNotify` 有三種方法，可以在不同時間呼叫。 如果您想要回應只是其中一種方法，您可以使用[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)類別，您不感興趣的方法會傳回 E_NOTIMPL。

當您建立資料列集時，您必須告訴提供者要傳回的資料列集物件，以支援`IConnectionPointContainer`，這設定所需的通知。

下列程式碼示範如何從 ATL 物件開啟資料列集，並使用`AtlAdvise`函式來設定通知接收。 `AtlAdvise` 您呼叫時，會使用 cookie 傳回`AtlUnadvise`。

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