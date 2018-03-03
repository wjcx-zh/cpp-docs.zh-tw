---
title: "使用 CSpinButtonCtrl |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSpinButtonCtrl
dev_langs:
- C++
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd1e652edb3501583624b068c604083f0c5d4165
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-cspinbuttonctrl"></a>使用 CSpinButtonCtrl
*微調按鈕*控制項 (也稱為*上下*控制項) 提供一對箭號，讓使用者可以按一下以調整值。 這個值稱為*目前位置*。 此位置會保持在微調按鈕的範圍內。 當使用者按一下向上箭號時，此位置會朝最大值移動，當使用者按一下向下箭號時，此位置會朝最小值移動。  
  
 微調按鈕控制項在 MFC 中的表示[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)類別。  
  
> [!NOTE]
>  根據預設，微調按鈕的範圍具有最大值為零 (0) 和最小值為 100。 因為最大值小於最小值，因此按一下向上箭號會遞減位置，按一下向下箭號會遞增位置。 使用[cspinbuttonctrl:: Setrange](../mfc/reference/cspinbuttonctrl-class.md#setrange)調整這些值。  
  
 通常，目前位置會顯示於附屬控制項中。 附屬控制項稱為*協同視窗*。 如需微調按鈕控制項的圖例，請參閱[關於上下按鈕控制項](http://msdn.microsoft.com/library/windows/desktop/bb759889)Windows SDK 中。  
  
 在 Visual Studio 中，若要建立一個微調控制項以及一個編輯控制項協同視窗，請先將編輯控制項加入至對話方塊或視窗，然後再拖曳微調控制項。 選取微調控制項並設定其**Auto Buddy**和**設定 Buddy Integer**屬性**True**。 也設定**對齊**屬性。**Right Align**最常見。 這些設定將編輯控制項設定為協同視窗，因為它的定位順序直接位在編輯控制項之前。 編輯控制項會顯示整數，而微調控制項會內嵌在編輯控制項的右邊。 （選擇性） 您可以透過設定微調控制項的有效範圍內[cspinbuttonctrl:: Setrange](../mfc/reference/cspinbuttonctrl-class.md#setrange)方法。 微調控制項和協同視窗之間不需要透過事件處理常式進行溝通，它們會直接交換資料。 如果您將微調控制項用於其他用途，例如，若要依據視窗和對話方塊的序列查看各個頁面，請加入 `UDN_DELTAPOS` 訊息的處理常式並在其中執行自訂動作。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [微調按鈕樣式](../mfc/spin-button-styles.md)  
  
-   [微調按鈕成員函式](../mfc/spin-button-member-functions.md)  
  
## <a name="see-also"></a>請參閱  
 [控制項](../mfc/controls-mfc.md)

