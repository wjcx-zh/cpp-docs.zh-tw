---
title: "CMultiLock Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMultiLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMultiLock class"
  - "synchronization objects, 存取控制"
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMultiLock Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

代表多執行緒程式用來控制多個資源存取的存取控制機制。  
  
## 語法  
  
```  
class CMultiLock  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMultiLock::CMultiLock](../Topic/CMultiLock::CMultiLock.md)|建構 `CMultiLock` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMultiLock::IsLocked](../Topic/CMultiLock::IsLocked.md)|判斷陣列中的指定同步物件是否已鎖定。|  
|[CMultiLock::Lock](../Topic/CMultiLock::Lock.md)|在某些的等候同步處理物件。|  
|[CMultiLock::Unlock](../Topic/CMultiLock::Unlock.md)|釋放所有附屬的同步物件。|  
  
## 備註  
 `CMultiLock` 不具有基底類別。  
  
 若要使用同步類別 [CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)和 [CEvent](../../mfc/reference/cevent-class.md)，您可以建立等候的 **CMultiLock** 或 [CSingleLock](../../mfc/reference/csinglelock-class.md) 物件並釋放同步處理物件。  請使用 **CMultiLock** ，當您有可能在特定時間使用的多個物件時。  當您在物件只需要一次時，請使用 `CSingleLock` 等候。  
  
 若要使用 **CMultiLock** 物件，請先建立同步處理的物件要等候。  接著，請在 10% 成員函式內的 **CMultiLock** 物件的建構函式在受控制資源的類別。  然後呼叫 [鎖定](../Topic/CMultiLock::Lock.md) 成員函式會判斷資源是否可用 \(表示\)。  如果是，則請繼續成員函式的其餘部分。  如果資源無法使用，請等候資源的一段指定的時間釋放或傳回失敗。  資源的使用完成後，請將呼叫 [解除鎖定](../Topic/CMultiLock::Unlock.md) 函式是否要重複使用 **CMultiLock** 物件，允許 **CMultiLock** 被終結的物件。  
  
 **CMultiLock** 物件最有用處，因為它能回應的執行緒有大量的 `CEvent` 物件時。  建立包含所有 `CEvent` 指標的陣列，並呼叫 `Lock`。  這會讓執行緒等待，直到其中一個事件發出信號。  
  
 如需如何使用 **CMultiLock** 物件的詳細資訊，請參閱本文 [多執行緒:如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 繼承階層架構  
 `CMultiLock`  
  
## 需求  
 **Header:** afxmt.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)