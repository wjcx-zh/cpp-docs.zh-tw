---
title: 滑桿控制項成員函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], methods
- slider controls [MFC], member functions
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3793ca47aa0537d5ca8d6858c165fc2c5ac64943
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="slider-control-member-functions"></a>滑桿控制項成員函式
應用程式可以呼叫滑桿控制項成員函式，來擷取滑桿控制項的相關資訊 ([CSliderCtrl](../mfc/reference/csliderctrl-class.md))，並變更其特性。  
  
 若要擷取滑桿 （也就是使用者已選擇的值） 的位置，請使用[GetPos](../mfc/reference/csliderctrl-class.md#getpos)成員函式。 若要設定滑桿的位置，使用[SetPos](../mfc/reference/csliderctrl-class.md#setpos)成員函式。 您可以隨時使用`VerifyPos`成員函式，並確認滑桿的最小和最大值之間。  
  
 滑桿控制項的範圍是一組連續的值可代表滑桿控制項。 大部分的應用程式使用[SetRange](../mfc/reference/csliderctrl-class.md#setrange)成員函式最初建立時設定滑桿控制項的範圍。 使用滑桿控制項建立之後，應用程式可以動態改變範圍[SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax)和[SetRangeMin](../mfc/reference/csliderctrl-class.md#setrangemin)成員函式。 當使用者完成使用滑桿控制項允許的範圍通常是以動態方式變更的應用程式會擷取最後的範圍設定。 若要擷取這些設定，請使用[GetRange](../mfc/reference/csliderctrl-class.md#getrange)， [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax)，和[GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin)成員函式。  
  
 應用程式可以使用`TBS_AUTOTICKS`能夠自動顯示的滑桿控制項刻度的樣式。 如果應用程式需要控制的位置或刻度標記的頻率，不過，可以使用許多成員函式。  
  
 若要設定刻度的位置，可以使用應用程式[SetTic](../mfc/reference/csliderctrl-class.md#settic)成員函式。 [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq)成員函式可讓應用程式設定刻度標記，都會出現在固定間隔在滑桿控制項的範圍內。 例如，應用程式可以使用此成員函式只限於 10 個刻度標記顯示 1 到 100 的範圍中。  
  
 若要擷取對應至的刻度標記的範圍中的索引，使用[GetTic](../mfc/reference/csliderctrl-class.md#gettic)成員函式。 [GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray)成員函式會擷取這些索引的陣列。 若要擷取的刻度標記，用戶端座標中的位置使用[GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos)成員函式。 應用程式可以使用擷取的刻度數目[GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics)成員函式。  
  
 [ClearTics](../mfc/reference/csliderctrl-class.md#cleartics)成員函式中移除所有滑桿控制項刻度標記。  
  
 滑桿控制項的列大小會決定應用程式接收時，滑桿移動的距離**TB_LINEDOWN**或**TB_LINEUP**通知訊息。 同樣地，頁面大小會決定回應**TB_PAGEDOWN**和**TB_PAGEUP**通知訊息。 應用程式可以擷取和使用設定的列和頁面大小值[GetLineSize](../mfc/reference/csliderctrl-class.md#getlinesize)， [SetLineSize](../mfc/reference/csliderctrl-class.md#setlinesize)， [GetPageSize](../mfc/reference/csliderctrl-class.md#getpagesize)，和[SetPageSize](../mfc/reference/csliderctrl-class.md#setpagesize)成員函式。  
  
 應用程式可用來擷取滑桿控制項的維度成員函式。 [GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect)成員函式會擷取滑桿的週框矩形。 [GetChannelRect](../mfc/reference/csliderctrl-class.md#getchannelrect)成員函式會擷取滑桿控制項的通道之周框。 （通道會是區域透過將滑桿移和其中包含反白顯示的選取範圍時）。  
  
 如果滑桿控制項具有`TBS_ENABLESELRANGE`樣式，使用者可以從中選取連續值的範圍。 成員函式的數字會允許進行動態調整選取範圍。 [SetSelection](../mfc/reference/csliderctrl-class.md#setselection)成員函式設定的開始和結束位置之選取範圍。 當使用者完成設定選取範圍時，應用程式可以擷取設定使用[GetSelection](../mfc/reference/csliderctrl-class.md#getselection)成員函式。 若要清除使用者的選取項目，使用[ClearSel](../mfc/reference/csliderctrl-class.md#clearsel)成員函式。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控制項](../mfc/controls-mfc.md)

