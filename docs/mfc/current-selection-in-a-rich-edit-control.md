---
title: "Rich Edit 控制項中的目前選取範圍 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a5f0d9332d1118809ae3d62c187ec848ec95ffbf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="current-selection-in-a-rich-edit-control"></a>Rich Edit 控制項中目前的選取範圍
使用者可以選取 rich edit 控制項中的文字 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 使用滑鼠或鍵盤。 目前的選取範圍是選取的字元的範圍或選取的任何字元的插入點的位置。 應用程式可以取得目前的選取範圍的相關資訊，設定目前的選取項目，判斷當目前的選取範圍變更和顯示或隱藏選取項目反白顯示。  
  
 若要判斷 rich edit 控制項中的目前選取範圍，請使用[GetSel](../mfc/reference/cricheditctrl-class.md#getsel)成員函式。 若要設定目前選取範圍，請使用[SetSel](../mfc/reference/cricheditctrl-class.md#setsel)成員函式。 [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885)結構具有這些函式用來指定字元範圍。 若要擷取目前的選取範圍的內容的相關資訊，您可以使用[GetSelectionType](../mfc/reference/cricheditctrl-class.md#getselectiontype)成員函式。  
  
 根據預設，rich edit 控制項顯示，並獲得和失去焦點時，會隱藏反白顯示的選取項目。 您可以顯示或隱藏反白顯示的選取項目在任何時候，使用[HideSelection](../mfc/reference/cricheditctrl-class.md#hideselection)成員函式。 例如，應用程式可能會提供 rich edit 控制項中尋找文字 [搜尋] 對話方塊。 應用程式可能會選取相符的文字，但不關閉對話方塊，在此情況下它必須使用`HideSelection`來反白顯示選取項目。  
  
 若要選取的文字在 rich edit 控制項中，使用[GetSelText](../mfc/reference/cricheditctrl-class.md#getseltext)成員函式。 將文字複製到指定的字元陣列。 您必須確定陣列足以容納選取的文字加上結束的 null 字元。  
  
 您可以使用搜尋字串 rich edit 控制項中[FindText](../mfc/reference/cricheditctrl-class.md#findtext)成員函式[FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909)結構搭配此函式指定要搜尋和要搜尋的字串的文字範圍。 您也可以指定這些選項做為搜尋是否區分大小寫。  
  
## <a name="see-also"></a>請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)

