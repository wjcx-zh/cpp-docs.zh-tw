---
title: "CMemoryState Structure | Microsoft Docs"
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
  - "CMemoryState"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMemoryState structure"
  - "偵測記憶體流失"
  - "記憶體遺漏, 偵測"
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMemoryState Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供便利的方式來偵測在程式的記憶體遺漏 \(Memory Leak\)。  
  
## 語法  
  
```  
struct CMemoryState  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMemoryState::CMemoryState](../Topic/CMemoryState::CMemoryState.md)|建構一個與類別的結構會控制記憶體檢查點。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMemoryState::Checkpoint](../Topic/CMemoryState::Checkpoint.md)|取得一個快照 \(檢查點\) 以目前記憶體狀態。|  
|[CMemoryState::Difference](../Topic/CMemoryState::Difference.md)|計算型別之間 `CMemoryState`兩個物件的差異。|  
|[CMemoryState::DumpAllObjectsSince](../Topic/CMemoryState::DumpAllObjectsSince.md)|傾印所有目前配置的物件摘要前一個檢查點。|  
|[CMemoryState::DumpStatistics](../Topic/CMemoryState::DumpStatistics.md)|列印 `CMemoryState` 物件的記憶體配置統計資料。|  
  
## 備註  
 `CMemoryState` 是結構，而且沒有基底類別。  
  
 「記憶體遺漏」時，物件的記憶體配置在堆積上，但是不會解除配置時何時不再需要。  這種記憶體遺漏最後可能會導致記憶體不足的錯誤。  有幾種方式配置和解除配置在程式中使用記憶體:  
  
-   使用函式 `malloc`\/**free** 系列從的執行階段程式庫。  
  
-   使用 Windows API 記憶體管理函式， **LocalAlloc**\/和\/**LocalFreeGlobalAllocGlobalFree**。  
  
-   使用 C\+\+ **new** 和 **刪除** 運算子。  
  
 使用時， **刪除**，同時又使用了， **new** 運算子所配置的記憶體不會解除配置只 `CMemoryState` 診斷有助於偵測造成的記憶體遺漏 \(Memory Leak\)。  記憶體管理函式的其他兩個群組是非 C\+\+ 程式，，和在同一個程式中使用它們 **new** 和 **刪除** 不建議使用混合。  當您需要記憶體配置時，檔案和行號的追蹤，提供額外的巨集， `DEBUG_NEW`取代 **new** 運算子。  使用`DEBUG_NEW` ，每當您通常會使用 **new** 運算子。  
  
 與其他診斷資訊， `CMemoryState` 診斷僅供偵錯您程式的發行版本。  偵錯版本必須定義 **\_DEBUG** 常數。  
  
 如果您懷疑程式有記憶體遺漏，您可以使用 `Checkpoint`、 **差異**和 `DumpStatistics` 函式尋找記憶體狀態 \(配置的物件之間的差異\)。在程式執行的兩個不同的點。  這項資訊有助於判斷它所配置的函式是否會清除所有的物件。  
  
 如果知道在配置和解除配置的失衡的何處發生未提供足夠的資訊，您可以使用 `DumpAllObjectsSince` 函式傾印配置的所有物件，因為前一個呼叫 `Checkpoint`。  這種傾印顯示配置順序、物件配置的原始程式檔和線條 \(如果您已設定使用 `DEBUG_NEW` \) 和物件的衍生，其位址和它的大小。  `DumpAllObjectsSince` 也會呼叫每個物件的 `Dump` 函式提供有關它的目前狀態的資訊。  
  
 如需如何使用 `CMemoryState` 和其他診斷的詳細資訊，請參閱 [偵錯 MFC 應用程式](../Topic/MFC%20Debugging%20Techniques.md)。  
  
> [!NOTE]
>  應該由 `#if defined(_DEBUG)/#endif`指示詞括住型別 `CMemoryState` 和呼叫物件的成員函式宣告為。  這在程式的偵錯組建造成記憶體診斷只包含。  
  
## 繼承階層架構  
 `CMemoryState`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)