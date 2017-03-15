---
title: "滑桿控制項成員函式 | Microsoft Docs"
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
  - "CSliderCtrl 類別, 方法"
  - "滑桿, 成員函式"
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 滑桿控制項成員函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

應用程式可以呼叫滑桿控制項的成員函式擷取有關滑桿控制項 \([CSliderCtrl](../mfc/reference/csliderctrl-class.md)\) 的資訊和變更其特性。  
  
 若要擷取滑桿 \(例如使用者選取了\) 值的位置，請使用 [GetPos](../Topic/CSliderCtrl::GetPos.md) 成員函式。  若要設定滑桿位置，請使用 [SetPos](../Topic/CSliderCtrl::SetPos.md) 成員函式。  任何時間。您可以使用 `VerifyPos` 成員函式，以確保滑桿在最小和最大值之間。  
  
 滑桿控制項的範圍是滑桿控制項可以表示的連續值。  在第一次建立時，大部分的應用程式使用 [SetRange](../Topic/CSliderCtrl::SetRange.md) 成員函式將滑桿控制項的範圍。  使用 [SetRangeMax](../Topic/CSliderCtrl::SetRangeMax.md) 和 [SetRangeMin](../Topic/CSliderCtrl::SetRangeMin.md) 成員函式，應用程式可以在滑桿控制項之後會動態修改範圍建立。  允許範圍動態典型變更應用程式擷取最終範圍設定，在使用者完成以滑桿控制項時。  若要擷取這些設定，請使用 [GetRange](../Topic/CSliderCtrl::GetRange.md)、 [GetRangeMax](../Topic/CSliderCtrl::GetRangeMax.md)和 [GetRangeMin](../Topic/CSliderCtrl::GetRangeMin.md) 成員函式。  
  
 應用程式可以使用 `TBS_AUTOTICKS` 樣式的滑桿控制項會自動顯示的刻度標記。  如果應用程式需要控制項的位置或刻度的頻率，不過，可以使用一些成員函式。  
  
 若要設定刻度標記的位置，應用程式可以使用 [SetTic](../Topic/CSliderCtrl::SetTic.md) 成員函式。  [SetTicFreq](../Topic/CSliderCtrl::SetTicFreq.md) 成員函式可讓應用程式設定定期出現滑桿控制項範圍的刻度標記。  例如，應用程式可以使用這個成員函式只顯示 10 個刻度標記在範圍 1 至 100。  
  
 若要擷取範圍的索引與刻度標記對應，請使用 [GetTic](../Topic/CSliderCtrl::GetTic.md) 成員函式。  [GetTicArray](../Topic/CSliderCtrl::GetTicArray.md) 成員函式來擷取這些索引。  若要擷取刻度標記的位置，以工作區座標，使用 [GetTicPos](../Topic/CSliderCtrl::GetTicPos.md) 成員函式。  使用 [GetNumTics](../Topic/CSliderCtrl::GetNumTics.md) 成員函式，應用程式可以擷取刻度標記數目。  
  
 [ClearTics](../Topic/CSliderCtrl::ClearTics.md) 成員函式中所有滑桿控制項的刻度標記。  
  
 當應用程式收到 **TB\_LINEDOWN** 和 **TB\_LINEUP** 通知訊息時，滑桿控制項行大小多遠判斷滑桿移動。  同樣地，頁面大小決定對 **TB\_PAGEDOWN** 和 **TB\_PAGEUP** 通知訊息的回應。  使用 [GetLineSize](../Topic/CSliderCtrl::GetLineSize.md)、 [SetLineSize](../Topic/CSliderCtrl::SetLineSize.md)、 [GetPageSize](../Topic/CSliderCtrl::GetPageSize.md)和 [SetPageSize](../Topic/CSliderCtrl::SetPageSize.md) 成員函式，應用程式可以擷取和設定線條和頁面大小值。  
  
 應用程式可以使用成員函式以取得滑桿控制項的大小。  [GetThumbRect](../Topic/CSliderCtrl::GetThumbRect.md) 成員函式以取得滑桿的週框。  [GetChannelRect](../Topic/CSliderCtrl::GetChannelRect.md) 成員函式以取得滑桿控制通道的週框。\(通道是滑桿移動，並反白顯示色彩的區域，當範圍已選取\)。  
  
 如果滑桿控制項有 `TBS_ENABLESELRANGE` 樣式，使用者可以選取連續值範圍從它。  允許選取範圍動態調整一些成員函式。  [SetSelection](../Topic/CSliderCtrl::SetSelection.md) 成員函式設定選取範圍的開始和結束位置。  當使用者完成設定選取範圍時，便會使用 [GetSelection](../Topic/CSliderCtrl::GetSelection.md) 成員函式，應用程式可以擷取設定。  若要清除使用者的選取範圍，請使用 [ClearSel](../Topic/CSliderCtrl::ClearSel.md) 成員函式。  
  
## 請參閱  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控制項](../mfc/controls-mfc.md)