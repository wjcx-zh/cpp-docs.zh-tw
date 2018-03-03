---
title: "對話方塊的生命週期 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 743aed312008d1908701933ec642dd52b0ac3ec8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="life-cycle-of-a-dialog-box"></a>對話方塊的生命週期
在對話方塊的生命週期，在使用者叫用對話方塊中，通常內建立並初始化對話方塊物件的命令處理常式，使用者互動對話方塊中，和對話框會關閉。  
  
 對於強制回應對話方塊，您的處理常式會收集任何使用者輸入之後對話框會關閉的資料。 因為對話方塊物件存在，其對話方塊視窗關閉之後，只要可以使用您的對話方塊類別的成員變數擷取資料。  
  
 非強制回應對話方塊，您可能會經常擷取資料從對話方塊物件，還是可以看到的對話方塊時。 在某些時候，對話方塊就會終結物件;當發生這種情況，取決於您的程式碼。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [建立和顯示對話方塊](../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [建立強制回應對話方塊](../mfc/creating-modal-dialog-boxes.md)  
  
-   [建立非強制回應對話方塊](../mfc/creating-modeless-dialog-boxes.md)  
  
-   [在記憶體中使用的對話方塊範本](../mfc/using-a-dialog-template-in-memory.md)  
  
-   [設定對話方塊的背景色彩](../mfc/setting-the-dialog-boxs-background-color.md)  
  
-   [初始化對話方塊](../mfc/initializing-the-dialog-box.md)  
  
-   [在對話方塊中的處理 Windows 訊息](../mfc/handling-windows-messages-in-your-dialog-box.md)  
  
-   [從對話方塊物件擷取資料](../mfc/retrieving-data-from-the-dialog-object.md)  
  
-   [關閉對話方塊](../mfc/closing-the-dialog-box.md)  
  
-   [終結對話方塊](../mfc/destroying-the-dialog-box.md)  
  
-   [對話方塊資料交換 (DDX) 和驗證 (DDV)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [屬性工作表對話方塊](../mfc/property-sheets-and-property-pages-mfc.md)  
  
## <a name="see-also"></a>請參閱  
 [對話方塊](../mfc/dialog-boxes.md)

