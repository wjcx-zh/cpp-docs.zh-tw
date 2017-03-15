---
title: "Multiple Dual Interfaces | Microsoft Docs"
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
  - "COM_INTERFACE_ENTRY_IID macro"
  - "COM_INTERFACE_ENTRY2 macro"
  - "雙重介面, exposing multiple"
  - "IDispatchImpl 類別, multiple dual interfaces"
  - "multiple dual interfaces"
  - "multiple dual interfaces, exposing with ATL"
ms.assetid: 7fea86e6-247f-4063-be6e-85588a9e3719
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Multiple Dual Interfaces
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可能希望將雙重介面 \(這也就是彈性的優點 vtable 和晚期繫結，讓類別能夠使用指令碼語言以及 C\+\+\) 具有多重繼承技術。  
  
 雖然公開一個 COM 物件的多個雙重介面是可行的，但不建議這樣做。  如果有多個雙重介面，只能有一 `IDispatch` 公開的介面。  可用的方法可確保這種情況會影響 \(例如函式或加入的程式碼複雜度遺失。  請考慮使用這種方法的開發人員應該仔細考量優缺點。  
  
## 公開單一 IDispatch 介面  
 以下列方式公開給單一物件的多個雙重介面能從 `IDispatchImpl`的兩個以上的特製化。  不過，因此，如果您允許用戶端用來 `IDispatch` 介面查詢，您必須使用 [COM\_INTERFACE\_ENTRY2](../Topic/COM_INTERFACE_ENTRY2.md) 巨集 \(或 [COM\_INTERFACE\_ENTRY\_IID](../Topic/COM_INTERFACE_ENTRY_IID.md)\) 指定要使用的基底類別 `IDispatch`的實作。  
  
 [!code-cpp[NVC_ATL_COM#23](../atl/codesnippet/CPP/multiple-dual-interfaces_1.h)]  
  
 由於只有一 `IDispatch` 介面公開，可以 `IDispatch` 介面只存取您物件的用戶端將無法存取方法或屬性在任何其他連接。  
  
## 合併多個雙重介面為基礎的唯一實作。  
 ATL 為合併多個雙重介面不提供任何支援加入至 `IDispatch`的唯一實作。  不過，有幾種已知的方法與手動合併介面，例如建立包含，建立新的物件執行 `QueryInterface` 函式 \(或使用巢狀物件以 typeinfo 的實作不同的 `IDispatch` 介面建立關聯 `IDispatch` 介面的樣板類別。  
  
 這些方法會有潛在的命名空間衝突的問題，以及程式碼的複雜度和維護性。  不建議您建立多個雙重介面。  
  
## 請參閱  
 [Dual Interfaces and ATL](../atl/dual-interfaces-and-atl.md)