---
title: "接收告知 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件 [C++], OLE DB 中的告知"
  - "告知 [C++], 事件"
  - "告知 [C++], OLE DB 消費者"
  - "OLE DB 消費者, 告知"
  - "OLE DB 提供者, 告知"
  - "接收 OLE DB 中的告知"
  - "資料列集, 事件告知"
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 接收告知
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB 會提供事件發生時負責接收告知的介面。  如需詳細資訊，請參閱《OLE DB 程式設計人員參考》的 [OLE DB 物件告知](https://msdn.microsoft.com/en-us/library/ms725406.aspx)。  這些事件的設定會使用標準 COM 連接點 \(Connection Point\) 機制。  例如，一個想要透過 `IRowsetNotify` 擷取事件的 ATL 物件，會將 `IRowsetNotify` 加入至類別衍生清單以實作 `IRowsetNotify` 介面，並透過 **COM\_INTERFACE\_ENTRY** 巨集以顯露這個介面。  
  
 `IRowsetNotify` 有三個可以在不同時間呼叫的方法。  如果您只想要回應其中一個方法，您可以使用 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) 類別，它會對您不感興趣的方法傳回 **E\_NOTIMPL**。  
  
 您必須在建立資料列集時，通知提供者您希望傳回的資料列集物件以支援 **IConnectionPointContainer** \(設定告知時需要使用到\)。  
  
 下列程式碼示範如何開啟 ATL 物件的資料列集，並使用 `AtlAdvise` 功能設定告知接收。  `AtlAdvise` 會傳回您在呼叫 `AtlUnadvise` 時所使用的 Cookie。  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
propset.AddProperty(DBPROP_IConnectionPointContainer, true);  
  
product.Open(session, _T("Products"), &propset);  
  
AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);  
```  
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)