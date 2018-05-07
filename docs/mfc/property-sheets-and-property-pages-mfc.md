---
title: 屬性工作表和屬性頁 (MFC) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 882b2d93ba7938017f64b1ad8fb8e680e0af42db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="property-sheets-and-property-pages-mfc"></a>屬性工作表和屬性頁 (MFC)
MFC[對話方塊](../mfc/dialog-boxes.md)可在上一個 「 索引標籤對話方塊 」 外觀加入屬性工作表和屬性頁。 在 MFC 中稱為 「 屬性工作表 」，這種對話方塊中，類似於 Microsoft Word、 Excel 和 Visual c + + 中，在許多對話方塊會出現含有索引標籤式的工作表，非常類似的檔案資料夾從前面到後面或一群重疊顯示視窗看到堆疊的堆疊。 [前端] 索引標籤上的控制項是可見的。只能加上標籤的索引標籤上會顯示背面的索引標籤。 屬性工作表是適合用來管理大量的屬性或恰當分為多個群組的設定。 一般而言，一個屬性工作表可以取代許多個別對話方塊以簡化使用者介面。  
  
 根據 MFC 4.0 版，屬性工作表和屬性頁會實作使用隨附於 Windows 95 及 Windows NT 3.51 版及更新版本的通用控制項。  
  
 使用類別來實作屬性工作表[CPropertySheet](../mfc/reference/cpropertysheet-class.md)和[CPropertyPage](../mfc/reference/cpropertypage-class.md) (述*MFC 參考*)。 `CPropertySheet` 定義整體的對話方塊中可包含多個 「 頁面 」 根據`CPropertyPage`。  
  
 如需建立和使用屬性工作表的資訊，請參閱主題[屬性工作表](../mfc/property-sheets-mfc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)   
 [屬性工作表和 MFC 中的屬性頁](../mfc/property-sheets-and-property-pages-in-mfc.md)   
 [交換資料](../mfc/exchanging-data.md)   
 [建立非強制回應屬性工作表](../mfc/creating-a-modeless-property-sheet.md)   
 [處理套用按鈕](../mfc/handling-the-apply-button.md)

