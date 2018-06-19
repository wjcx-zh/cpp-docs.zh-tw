---
title: 接收通知 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d9e1dee5c63281c729cdb798a190938c6433aac0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112312"
---
# <a name="receiving-notifications"></a>接收告知
OLE DB 提供介面來接收通知事件發生時。 這些述[OLE DB 物件通知](https://msdn.microsoft.com/en-us/library/ms725406.aspx)中*OLE DB 程式設計人員參考*。 這些事件的安裝程式會使用標準的 COM 連接點機制。 例如，想要擷取事件通過 ATL 物件`IRowsetNotify`實作`IRowsetNotify`介面加入`IRowsetNotify`類別衍生的清單，而且已公開其傳遞至**COM_INTERFACE_ENTRY**巨集。  
  
 `IRowsetNotify` 有三種方法，可以在不同時間呼叫。 如果您想要回應只是其中一種方法，您可以使用[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)類別，它會傳回**E_NOTIMPL**您不感興趣的方法。  
  
 當您建立資料列集時，您必須通知提供者想要傳回的資料列集物件，以支援**IConnectionPointContainer**，需要該資料行設定的通知。  
  
 下列程式碼示範如何從 ATL 物件開啟資料列集，並使用`AtlAdvise`設定通知接收函式。 `AtlAdvise` 當您呼叫時使用的 cookie 傳回`AtlUnadvise`。  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_IConnectionPointContainer, true);  
  

product.Open(session, _T("Products"), &propset);  
  

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);  
```  
  
## <a name="see-also"></a>另請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)