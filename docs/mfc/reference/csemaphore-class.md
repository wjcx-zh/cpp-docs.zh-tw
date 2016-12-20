---
title: "CSemaphore Class | Microsoft Docs"
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
  - "CSemaphore"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSemaphore class"
  - "號誌"
  - "synchronization objects, 號誌"
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSemaphore Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

類別 `CSemaphore` 物件代表「號誌」—允許限定數量的執行緒在一或多個處理序中存取的同步處理物件維護的執行緒數目的計數目前存取指定的資源。  
  
## 語法  
  
```  
class CSemaphore : public CSyncObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSemaphore::CSemaphore](../Topic/CSemaphore::CSemaphore.md)|建構 `CSemaphore` 物件。|  
  
## 備註  
 號誌是用在為只能支援的使用者數目有限的共用資源的存取權。  `CSemaphore` 物件目前的計數是其他使用者數目允許。  當計數到達零，任何嘗試使用 **CSemaphore** 物件控制項的資源就會插入到系統佇列，並在其或逾時或計算在 0 上引發事件。  一次可以存取受控制資源使用者的最大項目數。 `CSemaphore` 建構物件時指定。  
  
 會在需要時，要使用 **CSemaphore** 物件，請 `CSemaphore` 建構物件。  指定您要等候號誌的名稱，然後，您的應用程式應初始擁有它。  當建構函式傳回時，您可以存取該號誌。  但是，在進行存取控制資源時，請呼叫 [CSyncObject::Unlock](../Topic/CSyncObject::Unlock.md) 。  
  
 替代方法是使用 `CSemaphore` 要加入物件的型別 `CSemaphore` 的變數，您希望控制項類別的資料成員。  控制在建構物件時，請呼叫指定初始存取計數、最大存取號誌上的計數、名稱 \(如果它跨越處理序界限是使用\) 和想要的安全屬性的 `CSemaphore` 資料成員的建構函式。  
  
 若要存取 `CSemaphore` 物件做控制項的資源，請先在您的資源存取成員函式的型別 [CSingleLock](../../mfc/reference/csinglelock-class.md) 或型別 [CMultiLock](../../mfc/reference/cmultilock-class.md) 的變數。  然後呼叫鎖定物件的 `Lock` 成員函式 \(例如， [CSingleLock::Lock](../Topic/CSingleLock::Lock.md)\)。  此時，您的執行緒存取資源的存取權，會等候資源釋放並存取或等候資源釋放並計算時，不對資源的存取。  無論如何，您的資源存取以安全執行緒方法。  釋放資源，請使用鎖定物件的 `Unlock` 成員函式 \(例如， [CSingleLock::Unlock](../Topic/CSingleLock::Unlock.md)\)，或允許存取超出鎖定物件超出範圍。  
  
 或者，您也可以建立個別 **CSemaphore** 的物件，並在嘗試存取受控制資源明確存取它。  這個方法，不過，讀取原始程式碼的人的更清楚，比較容易發生錯誤。  
  
 如需如何使用 **CSemaphore** 物件的詳細資訊，請參閱本文 [多執行緒:如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CSemaphore`  
  
## 需求  
 **Header:** afxmt.h  
  
## 請參閱  
 [CSyncObject Class](../../mfc/reference/csyncobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)