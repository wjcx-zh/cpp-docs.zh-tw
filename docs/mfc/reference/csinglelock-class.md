---
title: "CSingleLock Class | Microsoft Docs"
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
  - "CSingleLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSingleLock class"
  - "synchronization objects, 存取控制"
  - "執行緒 [MFC], 存取控制"
  - "執行緒 [MFC], 同步"
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSingleLock Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

代表多執行緒程式用來控制單一資源存取的存取控制機制。  
  
## 語法  
  
```  
  
class CSingleLock  
  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSingleLock::CSingleLock](../Topic/CSingleLock::CSingleLock.md)|建構 `CSingleLock` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSingleLock::IsLocked](../Topic/CSingleLock::IsLocked.md)|判斷物件是否已鎖定。|  
|[CSingleLock::Lock](../Topic/CSingleLock::Lock.md)|在同步處理物件的時間。|  
|[CSingleLock::Unlock](../Topic/CSingleLock::Unlock.md)|發行同步處理物件。|  
  
## 備註  
 `CSingleLock` 不具有基底類別。  
  
 為了使用同步類別 [CSemaphore](../../mfc/reference/csemaphore-class.md)， [CMutex](../../mfc/reference/cmutex-class.md)、 [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)和 [CEvent](../../mfc/reference/cevent-class.md)，您必須建立 `CSingleLock` 或 [CMultiLock](../../mfc/reference/cmultilock-class.md) 物件等候和發行同步處理物件。  當您在物件只需要一次時，請使用 `CSingleLock` 等候。  請使用 **CMultiLock** ，當您有可能在特定時間使用的多個物件時。  
  
 若要使用 `CSingleLock` 物件，請呼叫其在 10% 成員函式內的建構函式在受控制資源的類別。  然後呼叫 [IsLocked](../Topic/CSingleLock::IsLocked.md) 成員函式會判斷資源是否可用。  如果是，請繼續成員函式的其餘部分。  如果資源無法使用，請等候資源的一段指定的時間釋放或傳回失敗。  資源的使用完成後，請將呼叫 [解除鎖定](../Topic/CSingleLock::Unlock.md) 函式是否要重複使用 `CSingleLock` 物件，允許 `CSingleLock` 被終結的物件。  
  
 `CSingleLock` 物件需要從 [CSyncObject](../../mfc/reference/csyncobject-class.md)衍生物件的外觀。  這通常是控制資源的類別的資料成員。  如需如何使用 `CSingleLock` 物件的詳細資訊，請參閱本文 [多執行緒:如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 繼承階層架構  
 `CSingleLock`  
  
## 需求  
 **Header:** afxmt.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMultiLock Class](../../mfc/reference/cmultilock-class.md)