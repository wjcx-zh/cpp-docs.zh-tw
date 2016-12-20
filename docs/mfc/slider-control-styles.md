---
title: "滑桿控制項樣式 | Microsoft Docs"
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
  - "CSliderCtrl 類別, 樣式"
  - "滑桿, 樣式"
  - "樣式, CSliderCtrl"
  - "樣式, 滑桿"
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 滑桿控制項樣式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

滑桿控制項 \([CSliderCtrl](../mfc/reference/csliderctrl-class.md)\) 可能具有垂直或水平方向。  它們可以在其中一側有刻度標記或兩側皆有或兩側皆沒有。  它們也可以用來指定連續值的範圍。  這些屬性由使用滑桿控制樣式控制，該樣式由您建立滑桿控制項指定。  
  
 `TBS_HORZ` 和 `TBS_VERT` 樣式判斷滑桿控制項的方向。  如果您不指定方向，滑桿控制項為水平方向。  
  
 `TBS_AUTOTICKS` 樣式建立有增量的刻度標記在它的值範圍的滑桿控制項。  當您呼叫 [SetRange](../Topic/CSliderCtrl::SetRange.md) 成員函式時，這些刻度標記會自動加入。  如果沒有指定 `TBS_AUTOTICKS`，您可以使用成員函式，例如 [SetTic](../Topic/CSliderCtrl::SetTic.md) 和 [SetTicFreq](../Topic/CSliderCtrl::SetTicFreq.md)，指定刻度標記的位置。  若要建立不顯示刻度標記的滑桿控制項，您可以使用 `TBS_NOTICKS` 樣式。  
  
 您可以顯示滑桿控制項的任一或兩方的刻度標記。  對於水平滑桿控制項，您可以指定 `TBS_BOTTOM` 或 `TBS_TOP` 模式。  對於垂直滑桿控制項，您可以指定 `TBS_RIGHT` 或 `TBS_LEFT` 模式。\(`TBS_BOTTOM` 和 `TBS_RIGHT` 為預設設定。\)對於滑桿控制項的兩側刻度標記會在所有方向，請指定 `TBS_BOTH` 樣式。  
  
 只有當您在建立時指定 `TBS_ENABLESELRANGE` 樣式，滑桿控制項可以顯示選取範圍。  當滑桿控制項樣式時，刻度標記會選取範圍的開始和結束位置顯示為三角形 \(而非垂直虛線\)，並選取範圍反白顯示。  例如，選取範圍可能適用於簡單的排程的應用程式。  使用者可以選取刻度標記的範圍與時數對應在一天識別排定會議的時間。  
  
 根據預設，當選取範圍變更時，滑桿控制項的滑桿長度變更。  如果滑桿控制項有 **TBS\_FIXEDLENGTH** 樣式，滑桿長度保持相同，即使選取範圍變更。  有 **TBS\_NOTHUMB** 樣式的滑桿控制項不包含滑桿。  
  
## 請參閱  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控制項](../mfc/controls-mfc.md)