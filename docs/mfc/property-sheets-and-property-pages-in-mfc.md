---
title: "屬性工作表和 MFC 中的屬性頁 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24a66bf9e062e43225827afdbb0bba45511c5f13
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>MFC 中的屬性工作表和屬性頁
屬性工作表，也稱為索引標籤對話方塊，為包含屬性頁的對話方塊。 每個屬性頁對話方塊範本資源為基礎，並包含的控制項。 加上最上層顯示 索引標籤。 [] 索引標籤命名頁面，並指出其用途。 使用者按一下來選取一組控制項的屬性工作表中的索引標籤。  
  
 使用頁面屬性工作表中的這些控制項聚集成有意義的集合。 包含的屬性工作表通常會有自己的數個控制項。 這些適用於所有頁面。  
  
 屬性工作表會根據類別[CPropertySheet](../mfc/reference/cpropertysheet-class.md)。 屬性頁根據類別[CPropertyPage](../mfc/reference/cpropertypage-class.md)。  
  
 屬性工作表是對話方塊的一種特殊的通常用來修改某些外部物件，例如在檢視中目前選取項目屬性。 屬性工作表有三個主要部分: [包含] 對話方塊中，一或多個屬性頁，顯示一次，一，每個頁面，使用者按一下以選取該頁面頂端的索引標籤。 屬性工作表可用於當您具有數個類似的群組的設定或變更的選項。 屬性工作表會將資訊分組易於了解的方式。  
  
> [!NOTE]
>  當您嘗試顯示屬性工作表使用`CPropertySheet::DoModal`，系統可能會產生第一個可能發生例外狀況。 發生這個例外狀況，因為系統嘗試變更[視窗樣式](../mfc/reference/styles-used-by-mfc.md#window-styles)之前已建立物件的物件。 如需此例外狀況，以及如何避免或處理的詳細資訊，請參閱[cpropertysheet:: Setwizardmode](../mfc/reference/cpropertysheet-class.md#domodal)。  
  
## <a name="see-also"></a>請參閱  
 [屬性工作表](../mfc/property-sheets-mfc.md)

