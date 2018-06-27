---
title: 微調按鈕樣式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 223b7e0875a5382edf5f4d350c9343d117768c41
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953774"
---
# <a name="spin-button-styles"></a>微調按鈕樣式
許多微調按鈕的設定 ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) 樣式所控制。 您可以設定下列樣式使用**屬性**對話方塊編輯器中的視窗。  
  
-   **方向**垂直或水平。 控制項的方向箭號按鈕。 相關聯的 UDS_HORZ 樣式。  
  
-   **對齊**未附加，左邊或右邊的其中一個。 控制微調按鈕的位置。 左邊和右邊位置微調按鈕旁協同視窗。 協同視窗的寬度勢必會縮小以容納微調按鈕。 相關聯的 UDS_ALIGNLEFT 和 UDS_ALIGNRIGHT 樣式。  
  
-   **Auto Buddy**為微調按鈕的協同視窗會自動選取疊置順序的前一個視窗。 在對話方塊範本中，這是位於定位順序中的微調按鈕控制項。 相關聯的 UDS_AUTOBUDDY 樣式。  
  
-   **設定 Buddy Integer**導致微調控制項遞增和遞減目前的位置變更為協同視窗的標題。 相關聯的 UDS_SETBUDDYINT 樣式。  
  
-   **No Thousands**不插入千位分隔符號的協同視窗標題中的值。 相關聯的 UDS_NOTHOUSANDS 樣式。  
  
    > [!NOTE]
    >  如果您想要使用對話方塊資料交換 (DDX) 以獲得協同控制項的整數值，請設定此樣式。 `DDX_Text` 不接受內嵌千位分隔符號。  
  
-   **自動換行**會造成 「 包裝 」 值會遞增或遞減超過控制項的範圍為位置。 相關聯的 UDS_WRAP 樣式。  
  
-   **方向鍵**會使微調按鈕遞增或遞減位置，當按下向上鍵和向下鍵。 相關聯的 UDS_ARROWKEYS 樣式。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [控制項](../mfc/controls-mfc.md)

