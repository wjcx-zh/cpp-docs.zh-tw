---
title: "剪貼簿流作業中 Rich Edit 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ec468b1f763e2f855f25fd8808d83605fb10673a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Rich Edit 控制項中的剪貼簿流作業
您的應用程式可以將剪貼簿內容貼至 rich edit 控制項 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 使用最適合使用剪貼簿格式或特定的剪貼簿格式。 您也可以判斷 Rich Edit 控制項是否可以貼上剪貼簿格式。  
  
 您可以複製或剪下目前的選取範圍的內容，使用[複製](../mfc/reference/cricheditctrl-class.md#copy)或[剪下](../mfc/reference/cricheditctrl-class.md#cut)成員函式。 同樣地，您可以貼入剪貼簿內容 rich edit 控制項使用[貼上](../mfc/reference/cricheditctrl-class.md#paste)成員函式。 控制項會先貼上其所辨識的第一個可用的格式，這大概會是最具描述性的格式。  
  
 若要將特定的剪貼簿格式，您可以使用[PasteSpecial](../mfc/reference/cricheditctrl-class.md#pastespecial)成員函式。 這個函式對於提供 Paste Special 命令，讓使用者選取剪貼簿格式的應用程式非常有幫助。 您可以使用[CanPaste](../mfc/reference/cricheditctrl-class.md#canpaste)成員函式，以判斷控制項是否已辨識指定的格式。  
  
 您也可以使用 `CanPaste` 來判斷 Rich Edit 控制項是否已辨識出可用的剪貼簿格。 這個函式適用於 `OnInitMenuPopup` 處理常式。 應用程式可能會根據控制項是否可貼上任何可用的格式來啟用或停用其貼上命令。  
  
 Rich Edit 控制項會註冊兩種剪貼簿格式：RTF 格式和所呼叫 RichEdit 文字和物件的格式。 應用程式可以使用註冊這些格式[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函式並指定**CF_RTF**和**CF_RETEXTOBJ**值。  
  
## <a name="see-also"></a>請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)

