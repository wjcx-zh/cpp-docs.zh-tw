---
title: "覆寫虛擬函式 （Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.virtualfunc.override
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 98e77579d511f4c78f0f7835c0b3c1dcea632734
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="overriding-a-virtual-function-visual-c"></a>覆寫 Virtual 函式 (Visual C++)
您可以覆寫虛擬函式定義在基底類別，從 Visual Studio[屬性 視窗](/visualstudio/ide/reference/properties-window)。  
  
### <a name="to-override-a-virtual-function-in-the-properties-window"></a>若要覆寫虛擬函式，在 [屬性] 視窗  
  
1.  在 類別檢視中，按一下 類別。  
  
2.  在 屬性 視窗中，按一下**會覆寫** 按鈕。  
  
    > [!NOTE]
    >  **會覆寫**按鈕時，使用您在 類別檢視 或 當您按一下來源視窗內選取的類別名稱。  
  
     左欄列出虛擬函式。 如果虛擬函式的名稱也會出現在右邊的資料行，然後覆寫已實作。  
  
3.  如果函式沒有覆寫，然後按一下 顯示建議的名稱，函式的 屬性 視窗右欄中的資料格會覆寫\<新增 >*FuncName*。  
  
4.  按一下以加入函式的虛設常式程式碼的建議的名稱。  
  
5.  若要編輯覆寫的函式，按兩下類別檢視中的函式名稱，然後編輯在來源視窗中的程式碼。  
  
 若要移除覆寫，請按一下右欄中的覆寫函式名稱，然後選取\<刪除 >*FuncName*。 函式的程式碼標記為註解。  
  
## <a name="see-also"></a>請參閱  
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)   
 [MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../ide/navigating-the-class-structure-visual-cpp.md)