---
title: "搭配使用影像清單與 Rebar 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "影像清單 [C++], Rebar 控制項"
  - "Rebar 控制項, 影像清單"
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 搭配使用影像清單與 Rebar 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每個 Rebar 群組列可以包含，尤其，從一個關聯的影像清單中的影像。  下列程序說明顯示的影像在 Rebar 群組列的必要步驟。  
  
### 針對 Rebar 群組列的顯示影像。  
  
1.  附加影像清單至 Rebar 控制項物件藉由呼叫 [SetImageList](../Topic/CReBarCtrl::SetImageList.md)，將指標傳遞給現有的影像清單。  
  
2.  修改 **REBARBANDINFO** 結構指派影像給 Rebar 群組列:  
  
    -   設定 **fMask** 成員給 **RBBIM\_IMAGE**，使用位元 OR 運算子視需要包含其他旗標。  
  
    -   設定 `iImage` 成員要顯示影像的影像清單索引。  
  
3.  初始化剩餘的資料成員，例如包含子視窗大小、文字和控制代碼，有必要的資訊。  
  
4.  插入新的群組列 \(使用影像\) 有對 [CReBarCtrl::InsertBand](../Topic/CReBarCtrl::InsertBand.md) 的呼叫，以傳遞 **REBARBANDINFO** 結構。  
  
 下列範例假設，具有兩個影像的現有影像清單物件附加至 Rebar 控制項物件 \(`m_wndReBar`\)。  新的 Rebar 群組列 \(由 `rbi`所定義\)，其中包含第一個影像，將使用呼叫 `InsertBand`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/CPP/using-an-image-list-with-a-rebar-control_1.cpp)]  
  
## 請參閱  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控制項](../mfc/controls-mfc.md)