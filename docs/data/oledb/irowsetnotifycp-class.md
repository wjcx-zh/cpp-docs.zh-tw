---
title: "IRowsetNotifyCP 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetNotifyCP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetNotifyCP 類別"
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# IRowsetNotifyCP 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作連接點介面 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)的提供者網站。  
  
## 語法  
  
```  
template <  
   class T,   
   class ReentrantEventSync = CComSharedMutex   
>  
class IRowsetNotifyCP :   
   public IConnectionPointImpl<  
      T,   
      piid = &__uuidof(IRowsetNotify),   
      CComDynamicUnkArray DynamicUnkArray  
   >,  
   public ReentrantEventSync  
```  
  
#### 參數  
 `T`  
 衍生自 `IRowsetNotifyCP`的類別。  
  
 `ReentrantEventSync`  
 支援重新進入的 Mutex 類別 \(預設為 **CComSharedMutex**\)。  Mutex 是允許執行緒對資源的互斥同步存取的物件。  
  
 `piid`  
 介面 ID 指標 \(**IID\***\) **IRowsetNotify** 連接點的介面。  預設值為 **&\_\_uuidof\(IRowsetNotify\)**。  
  
 `DynamicUnkArray`  
 陣列型別為 [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)，動態地配置了一些 **IUnknown** 指標到用戶端接收介面。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[Fire\_OnFieldChange](../../data/oledb/irowsetnotifycp-fire-onfieldchange.md)|通知變更的消費者對資料行中的值。|  
|[Fire\_OnRowChange](../../data/oledb/irowsetnotifycp-fire-onrowchange.md)|告知會影響資料列變更的消費者。|  
|[Fire\_OnRowsetChange](../../data/oledb/irowsetnotifycp-fire-onrowsetchange.md)|告知會影響整個資料列集變更的消費者。|  
  
## 備註  
 `IRowsetNotifyCP` 則實作廣播功能，以通知在 **IID\_IRowsetNotify** 連接點上的接聽程式關於資料列集內容的變更。  
  
 請注意您也必須實作和登錄在消費者 \(也稱為收到的\) `IRowsetNotify` 使用 [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) ，讓消費者處理通知。  如需實作連接點的 [接收通知](../../data/oledb/receiving-notifications.md) 連接在消費者。  
  
 如需實作告知的詳細資訊，請參閱 \< 支援通知 [建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)主題中。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Notifications \(COM\)](http://msdn.microsoft.com/library/windows/desktop/ms678433)   
 [Overview of Notifications \(OLE DB\)](https://msdn.microsoft.com/en-us/library/ms725406.aspx)   
 [BEGIN\_CONNECTION\_POINT\_MAP](../Topic/BEGIN_CONNECTION_POINT_MAP.md)   
 [END\_CONNECTION\_POINT\_MAP](../Topic/END_CONNECTION_POINT_MAP.md)   
 [CONNECTION\_POINT\_ENTRY](../Topic/CONNECTION_POINT_ENTRY.md)   
 [建立可更新的提供者](../../data/oledb/creating-an-updatable-provider.md)