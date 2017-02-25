---
title: "使用 CSpinButtonCtrl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CSpinButtonCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSpinButtonCtrl 類別, 使用"
  - "微調按鈕控制項"
  - "上下按鈕控制項"
  - "上下按鈕控制項, 微調按鈕控制項"
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 使用 CSpinButtonCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*微調按鈕* 控制項 \(也稱為 *上下* 按鈕控制項\) 提供使用者可按一下以調整值的一對箭號。  這個值就是 *目前的位置*。  位置保持在微調按鈕內的範圍。  當使用者按一下上箭號時，位置向最大值移動;然後，當使用者按一下向下箭號時，位置移動向最小值。  
  
 微調按鈕控制項在 MFC 由 [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) 類別表示。  
  
> [!NOTE]
>  根據預設，微調按鈕的範圍有最大值為零 \(0\) 和最小值設定為 100。  因為最大值小於最小值，按一下箭號減少位置，按一下向下箭號增加位置。  使用 [CSpinButtonCtrl::SetRange](../Topic/CSpinButtonCtrl::SetRange.md) 調整這些值。  
  
 通常，目前位置顯示於隨附的控制項。  隨附控制項稱為 *協同視窗*。  如需微調按鈕控制項的說明，請參閱 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [關於 Up\-Down 控制項](http://msdn.microsoft.com/library/windows/desktop/bb759889) 。  
  
 在 Visual Studio 中，若要建立微調控制項，以及一個編輯控制項的協同視窗，首先將編輯控制項加入至對話方塊或視窗，然後拖曳微調控制項。  選取微調控制項並將其 \[**自動協同**\] 和 \[**設定協同整數**\] 屬性設定為 \[**true**\]。  同時設定 \[**對齊**\] 屬性; \[**向右對齊**\] 最常見。  這些設定，因為它直接在編輯控制項的定位順序之前，編輯控制項設定為協同視窗。  編輯控制項顯示整數，以及微調控制項內嵌在編輯控制項的右邊。  或者，您可以利用 [CSpinButtonCtrl::SetRange](../Topic/CSpinButtonCtrl::SetRange.md) 方法設定微調控制項的有效範圍。  不需要事件處理常式以在微調控制項和協同視窗之間溝通，因為它們直接交換資料。  如果您為其他用途，例如，透過 Windows 序列呼叫使用微調控制項或對話方塊，請加入 `UDN_DELTAPOS` 訊息的處理常式並在那裡執行自訂動作。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [微調按鈕樣式](../mfc/spin-button-styles.md)  
  
-   [微調按鈕成員函式](../mfc/spin-button-member-functions.md)  
  
## 請參閱  
 [控制項](../mfc/controls-mfc.md)