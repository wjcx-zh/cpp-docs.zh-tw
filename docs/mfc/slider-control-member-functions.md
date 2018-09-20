---
title: 滑桿控制項成員函式 |Microsoft Docs
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
ms.openlocfilehash: 6f3c7c9d2b1cfd863f2c76a6f0ce9de197912786
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377509"
---
# <a name="slider-control-member-functions"></a>滑桿控制項成員函式

應用程式可以呼叫滑桿控制項成員函式，以擷取滑桿控制項的相關資訊 ([CSliderCtrl](../mfc/reference/csliderctrl-class.md))，並變更其特性。

若要擷取滑桿 （也就是使用者已選擇的值） 的位置，請使用[GetPos](../mfc/reference/csliderctrl-class.md#getpos)成員函式。 若要設定滑桿的位置，使用[SetPos](../mfc/reference/csliderctrl-class.md#setpos)成員函式。 您可以隨時使用`VerifyPos`成員函式，並確認滑桿的最小和最大值之間。

滑桿控制項的範圍是一組連續的值，可代表滑桿控制項。 大部分的應用程式會使用[SetRange](../mfc/reference/csliderctrl-class.md#setrange)最初建立時設定的範圍滑桿控制項成員函式。 應用程式可以動態變更範圍，使用一經建立滑桿控制項[SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax)並[SetRangeMin](../mfc/reference/csliderctrl-class.md#setrangemin)成員函式。 當使用者已完成使用滑桿控制項允許的範圍通常是以動態方式變更的應用程式會擷取最後的範圍設定。 若要擷取這些設定，請使用[GetRange](../mfc/reference/csliderctrl-class.md#getrange)， [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax)，並[GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin)成員函式。

應用程式可以使用 TBS_AUTOTICKS 樣式，將滑桿控制項刻度標記會自動顯示。 如果應用程式需要控制的位置或刻度標記的頻率，不過，可以使用幾個成員函式。

若要設定的刻度標記位置，可以使用應用程式[SetTic](../mfc/reference/csliderctrl-class.md#settic)成員函式。 [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq)成員函式可讓應用程式設定刻度標記，都會出現在定期間隔滑桿控制項的範圍內。 比方說，應用程式也可以使用此成員函式，以顯示只有 10 個刻度在 1 到 100 的範圍內。

若要擷取對應至刻度標記的範圍中的索引，請使用[GetTic](../mfc/reference/csliderctrl-class.md#gettic)成員函式。 [GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray)成員函式會擷取這些索引的陣列。 若要擷取的刻度標記，用戶端座標中的位置使用[GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos)成員函式。 應用程式可以使用擷取的刻度數目[GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics)成員函式。

[ClearTics](../mfc/reference/csliderctrl-class.md#cleartics)成員函式會移除所有的滑桿控制項刻度標記。

滑桿控制項的列大小會決定多久滑桿移動應用程式收到 TB_LINEDOWN 或 TB_LINEUP 通知訊息時。 同樣地，頁面大小會決定 TB_PAGEDOWN 和 TB_PAGEUP 通知訊息的回應。 應用程式可以擷取並使用設定的列和頁面大小值[GetLineSize](../mfc/reference/csliderctrl-class.md#getlinesize)， [SetLineSize](../mfc/reference/csliderctrl-class.md#setlinesize)， [GetPageSize](../mfc/reference/csliderctrl-class.md#getpagesize)，和[SetPageSize](../mfc/reference/csliderctrl-class.md#setpagesize)成員函式。

應用程式可用來擷取維度的滑桿控制項成員函式。 [GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect)成員函式會擷取滑桿的周框矩形。 [GetChannelRect](../mfc/reference/csliderctrl-class.md#getchannelrect)成員函式會擷取滑桿控制項的通道的周框矩形。 （通道會是區域滑桿移和其中包含反白顯示的選取範圍時）。

如果滑桿控制項具有 TBS_ENABLESELRANGE 樣式，使用者可以從中選取連續值的範圍。 許多成員函式都允許進行動態調整選取範圍。 [SetSelection](../mfc/reference/csliderctrl-class.md#setselection)成員函式設定的起始和結束位置之選取範圍。 當使用者完成設定選取範圍時，應用程式可以擷取設定使用[GetSelection](../mfc/reference/csliderctrl-class.md#getselection)成員函式。 若要清除使用者的選取項目，請使用[ClearSel](../mfc/reference/csliderctrl-class.md#clearsel)成員函式。

## <a name="see-also"></a>另請參閱

[使用 CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

