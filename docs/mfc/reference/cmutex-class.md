---
title: "CMutex Class | Microsoft Docs"
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
  - "Mutex"
  - "CMutex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMutex class"
  - "mutex"
  - "同步類別, CMutex class"
  - "synchronization objects, mutex"
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMutex Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示「Mutex」—允許一個執行緒存取資源互斥 \(Mutually Exclusive\) 存取的同步處理物件。  
  
## 語法  
  
```  
class CMutex : public CSyncObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMutex::CMutex](../Topic/CMutex::CMutex.md)|建構 `CMutex` 物件。|  
  
## 備註  
 在中，只有一個執行緒可以同時允許修改資料或某些其他控制資源時， Mutex 就很有用。  例如，將節點加入至連結的清單是應該由一個執行緒一次只允許的處理序。  您可以使用控制項連結串列的 `CMutex` 物件，只有一個執行緒可以對清單中每個的存取權。  
  
 會在需要時，要使用 `CMutex` 物件，請 `CMutex` 建構物件。  指定您要等候 Mutex 的名稱，然後，您的應用程式應初始擁有它。  當建構函式傳回時，您可以存取該 Mutex。  但是，在進行存取控制資源時，請呼叫 [CSyncObject::Unlock](../Topic/CSyncObject::Unlock.md) 。  
  
 替代方法是使用 `CMutex` 要加入物件的型別 `CMutex` 的變數，您希望控制項類別的資料成員。  控制在建構物件時，請呼叫 `CMutex` 資料成員會指定是否擁有 Mutex 一開始，名稱的 Mutex \(如果跨越處理序界限是使用\) 和想要的安全屬性的建構函式。  
  
 若要存取 `CMutex` 物件做控制項的資源，請先在您的資源存取成員函式的型別 [CSingleLock](../../mfc/reference/csinglelock-class.md) 或型別 [CMultiLock](../../mfc/reference/cmultilock-class.md) 的變數。  然後呼叫鎖定物件的 `Lock` 成員函式 \(例如， [CSingleLock::Lock](../Topic/CSingleLock::Lock.md)\)。  此時，您的執行緒存取資源的存取權，會等候資源釋放並存取或等候資源釋放並計算時，不對資源的存取。  無論如何，您的資源存取以安全執行緒方法。  釋放資源，請使用鎖定物件的 `Unlock` 成員函式 \(例如， [CSingleLock::Unlock](../Topic/CSingleLock::Unlock.md)\)，或允許存取超出鎖定物件超出範圍。  
  
 如需使用 `CMutex` 物件的詳細資訊，請參閱本文 [多執行緒:如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CMutex`  
  
## 需求  
 **Header:** afxmt.h  
  
## 請參閱  
 [CSyncObject Class](../../mfc/reference/csyncobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)