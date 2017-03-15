---
title: "進度控制項的樣式 | Microsoft Docs"
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
  - "CProgressCtrl 類別, 樣式"
  - "PBS_SMOOTH 樣式"
  - "PBS_VERTICAL 樣式"
  - "進度控制項 [C++], 樣式"
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 進度控制項的樣式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您一開始建立進度控制項 \([CProgressCtrl::Create](../Topic/CProgressCtrl::Create.md)\) 時，請使用 `dwStyle` 參數為進度控制項指定所需的視窗樣式。  下列清單說明適用的視窗樣式。  控制項會忽略除了此清單以外的所有視窗樣式。  您必須建立控制項當做子視窗，並且通常以對話方塊為父代。  
  
|視窗樣式|作用|  
|----------|--------|  
|`WS_BORDER`|在視窗周圍建立框線。|  
|**WS\_CHILD**|建立子視窗 \(應永遠為 `CProgressCtrl` 所使用\)。|  
|**WS\_CLIPCHILDREN**|在父視窗內繪圖時，應排除子視窗佔用的區域。  在建立父視窗時使用。|  
|**WS\_CLIPSIBLINGS**|裁剪相對於其他的子視窗。|  
|**WS\_DISABLED**|建立一個一開始即停用的視窗。|  
|**WS\_VISIBLE**|建立一個一開始即可見的視窗。|  
|**WS\_TABSTOP**|指定控制項在使用者按下 TAB 鍵並移至它時可以接收焦點。|  
  
 此外，您可以指定兩個樣式 \(`PBS_VERTICAL` 和 `PBS_SMOOTH`\) 只適用於進度控制項。  
  
 使用 `PBS_VERTICAL` 垂直放置控制項，而非水平。  使用 `PBS_SMOOTH` 完全填滿控制項，而不是顯示重複填滿控制項的小方塊。  
  
 沒有 `PBS_SMOOTH` 樣式：  
  
 ![標準進度列樣式](../mfc/media/vc4ruw1.png "vc4RUW1")  
  
 有 `PBS_SMOOTH` 和 `PBS_VERTICAL` 樣式：  
  
 ![進度列樣式：平滑和垂直](../mfc/media/vc4ruw2.png "vc4RUW2")  
  
 如需詳細資訊，請參閱 *MFC 參考* 的 [視窗樣式](../mfc/reference/frame-window-styles-mfc.md)。  
  
## 請參閱  
 [使用 CProgressCtrl](../mfc/using-cprogressctrl.md)