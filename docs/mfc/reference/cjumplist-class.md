---
title: "CJumpList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxadv/CJumpList"
  - "CJumpList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CJumpList class"
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# CJumpList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當您在工作列中的圖示，以滑鼠右鍵按一下 `CJumpList` 是顯示項目的快速鍵的清單。  
  
## 語法  
  
```  
class CJumpList;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CJumpList::CJumpList](../Topic/CJumpList::CJumpList.md)|建構 `CJumpList` 物件。|  
|[CJumpList::~CJumpList](../Topic/CJumpList::~CJumpList.md)|終結 `CJumpList` 物件。|  
  
|名稱|描述|  
|--------|--------|  
|[CJumpList::AbortList](../Topic/CJumpList::AbortList.md)|放棄一種建置清單的交易，而且不會執行。|  
|[CJumpList::AddDestination](../Topic/CJumpList::AddDestination.md)|多載。  將項目加入至清單中。|  
|[CJumpList::AddKnownCategory](../Topic/CJumpList::AddKnownCategory.md)|附加已知的類別加入至清單。|  
|[CJumpList::AddTask](../Topic/CJumpList::AddTask.md)|多載。  將項目加入至標準工作分類。|  
|[CJumpList::AddTasks](../Topic/CJumpList::AddTasks.md)|將項目加入至標準工作分類。|  
|[CJumpList::AddTaskSeparator](../Topic/CJumpList::AddTaskSeparator.md)|將在工作之間的分隔符號。|  
|[CJumpList::ClearAll](../Topic/CJumpList::ClearAll.md)|移除到目前為止已經加入至 `CJumpList` 目前執行個體的所有工作和目標。|  
|[CJumpList::ClearAllDestinations](../Topic/CJumpList::ClearAllDestinations.md)|移除到目前為止已經加入至 `CJumpList` 目前執行個體的所有目的。|  
|[CJumpList::CommitList](../Topic/CJumpList::CommitList.md)|結束一個建置清單的異動並認可這個報告目錄重新命名這個關聯的存放區 \(註冊在這種情況下\)。|  
|[CJumpList::GetDestinationList](../Topic/CJumpList::GetDestinationList.md)|擷取介面指標的清單。|  
|[CJumpList::GetMaxSlots](../Topic/CJumpList::GetMaxSlots.md)|擷取項目的最大數目，包括在呼叫應用程式的目的功能表可以顯示的分類標題。|  
|[CJumpList::GetRemovedItems](../Topic/CJumpList::GetRemovedItems.md)|表示已移除之目的傳回項目陣列。|  
|[CJumpList::InitializeList](../Topic/CJumpList::InitializeList.md)|開始一個建置清單的交易。|  
|[CJumpList::SetAppID](../Topic/CJumpList::SetAppID.md)|設定要建立的清單的應用程式模型的使用者 ID。|  
  
## 繼承階層架構  
 [CJumpList](../../mfc/reference/cjumplist-class.md)  
  
## 需求  
 **標題:** afxadv.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)