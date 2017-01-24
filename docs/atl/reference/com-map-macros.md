---
title: "COM Map Macros | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM 介面, COM map macros"
ms.assetid: 0f33656d-321f-4996-90cc-9a7f21ab73c3
caps.latest.revision: 16
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COM Map Macros
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這些巨集定義 COM 介面對應。  
  
|||  
|-|-|  
|[BEGIN\_COM\_MAP](../Topic/BEGIN_COM_MAP.md)|標記 COM 介面對應項目的開頭。|  
|[COM\_INTERFACE\_ENTRY](../Topic/COM_INTERFACE_ENTRY%20Macros.md)|輸入介面的 COM 介面對應。|  
|[COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md)|使用這個巨集會區分繼承自兩個分支。|  
|[COM\_INTERFACE\_ENTRY\_IID](../Topic/COM_INTERFACE_ENTRY_IID.md)|使用這個巨集輸入至 COM 介面對應並指定它的 IID。|  
|[COM\_INTERFACE\_ENTRY2\_IID](../Topic/COM_INTERFACE_ENTRY2_IID.md)|和 [COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md)，不過，您可以指定不同的 IID。|  
|[COM\_INTERFACE\_ENTRY\_AGGREGATE](../Topic/COM_INTERFACE_ENTRY_AGGREGATE.md)|當 `iid` 判斷的介面來查詢，會 `punk`的 `COM_INTERFACE_ENTRY_AGGREGATE` 轉送。|  
|[COM\_INTERFACE\_ENTRY\_AGGREGATE\_BLIND](../Topic/COM_INTERFACE_ENTRY_AGGREGATE_BLIND.md)|和 [COM\_INTERFACE\_ENTRY\_AGGREGATE](../Topic/COM_INTERFACE_ENTRY_AGGREGATE.md)，不過，查詢在順向查詢的任何 IID 結果的效果相同。 `punk`。|  
|[COM\_INTERFACE\_ENTRY\_AUTOAGGREGATE](../Topic/COM_INTERFACE_ENTRY_AUTOAGGREGATE.md)|和 [COM\_INTERFACE\_ENTRY\_AGGREGATE](../Topic/COM_INTERFACE_ENTRY_AGGREGATE.md)相同，不過，如果 `punk` 是 **NULL**，就會自動建立 `clsid`描述的彙總。|  
|[COM\_INTERFACE\_ENTRY\_AUTOAGGREGATE\_BLIND](../Topic/COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND.md)|和 [COM\_INTERFACE\_ENTRY\_AUTOAGGREGATE](../Topic/COM_INTERFACE_ENTRY_AUTOAGGREGATE.md)，但是有一點例外，就是查詢任何 IID 的相同導致轉送至查詢 `punk`，而且，如果是 `punk`**NULL**，自動建立 `clsid`描述的彙總。|  
|[COM\_INTERFACE\_ENTRY\_BREAK](../Topic/COM_INTERFACE_ENTRY_BREAK.md)|在指定的介面上查詢時，會造成程式呼叫 [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297) 。|  
|[COM\_INTERFACE\_ENTRY\_CACHED\_TEAR\_OFF](../Topic/COM_INTERFACE_ENTRY_CACHED_TEAR_OFF.md)|儲存使用者專屬的每個執行個體的資料。|  
|[COM\_INTERFACE\_ENTRY\_TEAR\_OFF](../Topic/COM_INTERFACE_ENTRY_TEAR_OFF.md)|公開 \(Expose\) Tear\-Off 介面。|  
|[COM\_INTERFACE\_ENTRY\_CHAIN](../Topic/COM_INTERFACE_ENTRY_CHAIN.md)|表示處理到達 COM 對應時，這個項目的處理基底類別的 COM 對應。|  
|[COM\_INTERFACE\_ENTRY\_FUNC](../Topic/COM_INTERFACE_ENTRY_FUNC.md)|攔截到 ATL 的 `QueryInterface` 邏輯的一般機制。|  
|[COM\_INTERFACE\_ENTRY\_FUNC\_BLIND](../Topic/COM_INTERFACE_ENTRY_FUNC_BLIND.md)|和 [COM\_INTERFACE\_ENTRY\_FUNC](../Topic/COM_INTERFACE_ENTRY_FUNC.md)，不過，查詢在呼叫的任何 IID 結果的效果相同。 `func`。|  
|[COM\_INTERFACE\_ENTRY\_NOINTERFACE](../Topic/COM_INTERFACE_ENTRY_NOINTERFACE.md)|在指定的介面上查詢時，會傳回 **E\_NOINTERFACE** 並結束處理 COM 對應。|  
|[END\_COM\_MAP](../Topic/END_COM_MAP.md)|標記 COM 介面對應項目的結尾。|  
  
## 請參閱  
 [Macros](../../atl/reference/atl-macros.md)   
 [COM Map Global Functions](../../atl/reference/com-map-global-functions.md)