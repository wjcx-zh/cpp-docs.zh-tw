---
title: "CEvent Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CEvent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEvent class"
  - "同步類別, CEvent class"
  - "synchronization objects, event"
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CEvent Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示事件，是同步物件可讓執行緒向類別上的事件發生。  
  
## 語法  
  
```  
class CEvent : public CSyncObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CEvent::CEvent](../Topic/CEvent::CEvent.md)|建構 `CEvent` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CEvent::PulseEvent](../Topic/CEvent::PulseEvent.md)|將事件設定為可用 \(信號\) 版本，等候執行緒的和集合事件為無法使用 \(非\)。|  
|[CEvent::ResetEvent](../Topic/CEvent::ResetEvent.md)|將事件設定為無法使用 \(非\)。|  
|[CEvent::SetEvent](../Topic/CEvent::SetEvent.md)|將事件加入至可用 \(信號\) 和釋放所有等候中的執行緒。|  
|[CEvent::Unlock](../Topic/CEvent::Unlock.md)|發行事件物件。|  
  
## 備註  
 指定執行緒時必須知道執行其工作時，事件會很有用處。  例如，複製至資料檔案的執行緒必須告知，當新資料可用時。  您可以使用告知複本的 `CEvent` 物件執行緒，新增資料可用，執行緒可以儘快執行其工作。  
  
 `CEvent` 具有兩種類型:手動和自動。  
  
 將自動 `CEvent` 物件自動復原為未收到信號的 \(無法使用\) 狀態，在釋放之後至少一個執行緒。  根據預設，在中，除非您在建構時，您可以 `bManualReset` 參數的 `TRUE``CEvent` 物件會自動進行。  
  
 方針 `CEvent` 物件在 [SetEvent](../Topic/CEvent::SetEvent.md) 或 [ResetEvent](../Topic/CEvent::ResetEvent.md) 設定的狀態會暫停，直到另一個函式呼叫。  若要建立手動 `CEvent` 物件，請在建構期間傳遞 `bManualReset` 參數的 `TRUE` 。  
  
 如果需要時，要使用 `CEvent` 物件，請 `CEvent` 建構物件。  指定要等候事件的名稱，並指定您的應用程式應初始擁有它。  當建構函式傳回時，您可以存取事件。  呼叫 [SetEvent](../Topic/CEvent::SetEvent.md) 信號 \(可提供事件\) 物件，然後呼叫 [解除鎖定](../Topic/CEvent::Unlock.md) 在進行存取控制資源時。  
  
 替代方法是使用 `CEvent` 要加入物件的型別 `CEvent` 的變數時，您要將控制項的類別的資料成員。  控制在建構物件時，請呼叫 `CEvent` 資料成員的建構函式並指定事件是否一開始就會收到信號，因此的事件物件的 specifythe 型別時，事件的名稱 \(如果它跨越處理序界限是使用\) 和所有需要的安全性屬性。  
  
 若要存取 `CEvent` 物件做控制項的資源，請先建立型別 [CSingleLock](../../mfc/reference/csinglelock-class.md) 的變數或輸入於資源存取方法的 [CMultiLock](../../mfc/reference/cmultilock-class.md) 。  然後呼叫鎖定物件 \(例如， [CMultiLock::Lock](../Topic/CMultiLock::Lock.md)\) 的 `Lock` 方法。  此時，您的執行緒存取資源的存取權，會等候資源釋放並存取或等候資源釋放，時間和錯誤才能存取資源。  無論如何，您的資源存取以安全執行緒方法。  若要釋放資源，請呼叫 `SetEvent` 事件發出信號物件，然後使用鎖定物件的 `Unlock` 方法 \(例如， [CMultiLock::Unlock](../Topic/CMultiLock::Unlock.md)\)，或是讓鎖定物件落在範圍外。  
  
 如需如何使用 `CEvent` 物件的詳細資訊，請參閱 [多執行緒：如何使用同步類別](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 範例  
 [!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/CPP/cevent-class_1.cpp)]  
  
 [!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/CPP/cevent-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CEvent`  
  
## 需求  
 **Header:** afxmt.h  
  
## 請參閱  
 [CSyncObject Class](../../mfc/reference/csyncobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)