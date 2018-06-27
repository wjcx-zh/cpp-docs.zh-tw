---
title: 滑桿控制項樣式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f76fbe9f85d978a5c2865b48720588b620508a07
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951048"
---
# <a name="slider-control-styles"></a>滑桿控制項樣式
滑桿控制項 ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) 可以具有垂直或水平方向。 它們可以在其中一側具有刻度標記，或兩側皆有或兩側皆沒有。 它們也可以用來指定連續值的範圍。 這些屬性是藉由使用滑桿控制樣式來控制，您在建立滑桿控制項時會指定該樣式。  
  
 TBS_HORZ 和 TBS_VERT 樣式會判斷滑桿控制項的方向。 如果您不指定方向，滑桿控制項會是水平方向。  
  
 TBS_AUTOTICKS 樣式建立的滑桿控制項在其範圍值中有每個增量的刻度。 當您呼叫時自動加入這些刻度[SetRange](../mfc/reference/csliderctrl-class.md#setrange)成員函式。 如果您未指定 TBS_AUTOTICKS，您可以使用成員函式，例如[SetTic](../mfc/reference/csliderctrl-class.md#settic)和[SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq)，以指定的刻度標記位置。 若要建立不顯示刻度標記的滑桿控制項，您可以使用 TBS_NOTICKS 樣式。  
  
 您可以在滑桿控制項的任一或兩側顯示刻度標記。 對於水平滑桿控制項，您可以指定 TBS_BOTTOM 或 TBS_TOP 樣式。 對於垂直滑桿控制項，您可以指定 TBS_RIGHT 或 TBS_LEFT 樣式。 （TBS_BOTTOM 和 TBS_RIGHT 是預設設定）。刻度滑桿控制項，以任何方向的兩端，指定 TBS_BOTH 樣式。  
  
 只有當您在建立時，指定 TBS_ENABLESELRANGE 樣式，滑桿控制項可以顯示選取範圍。 當滑桿控制項具有此樣式時，刻度標記會位於選取範圍的開始和結束位置，顯示為三角形 (而非垂直虛線)，並會反白顯示選取範圍。 例如，選取範圍可能適用於簡單的排程應用程式。 使用者可以選取對應一天內小時數的刻度標記範圍來識別排定會議的時間。  
  
 根據預設，滑桿控制項的滑桿長度會隨著選取範圍而變更。 如果滑桿控制項具有 TBS_FIXEDLENGTH 樣式，滑桿的長度會保持相同即使選取範圍已變更。 TBS_NOTHUMB 樣式的滑桿控制項不包含滑桿。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控制項](../mfc/controls-mfc.md)

