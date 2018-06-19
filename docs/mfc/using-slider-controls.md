---
title: 使用滑桿控制項 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9180d792f38652b22f430e497ef0e42dc54f6d73
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382176"
---
# <a name="using-slider-controls"></a>使用滑桿控制項
滑桿控制項的一般使用方式會遵循下列模式：  
  
-   建立控制項。 如果在對話方塊範本中指定控制項，就會隨對話方塊的建立而自動建立。 (您應該有[CSliderCtrl](../mfc/reference/csliderctrl-class.md)您對應至滑桿控制項的對話方塊類別中的成員。)或者，您可以使用[建立](../mfc/reference/csliderctrl-class.md#create)做為任何視窗的子視窗建立控制項的成員函式。  
  
-   呼叫各種 Set 成員函式以設定控制項的值。 您可以進行的變更包括設定滑桿的最小和最大位置、繪製刻度標記、設定選取範圍，以及重新調整滑桿定位。 若要這樣做的好時機是在對話方塊的控制項在對話方塊中， [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)函式。  
  
-   當使用者與控制項互動時，它會傳送各種通知訊息。 您可以從控制項擷取滑桿值，藉由呼叫[GetPos](../mfc/reference/csliderctrl-class.md#getpos)成員函式。  
  
-   當完成控制項時，須確定您已正確地終結。 如果滑桿控制項在對話方塊中，將會自動終結和 `CSliderCtrl` 物件。 否則，您必須確保控制項和 `CSliderCtrl` 物件都已正確地終結。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控制項](../mfc/controls-mfc.md)

