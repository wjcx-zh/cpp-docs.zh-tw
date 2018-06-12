---
title: 覆寫虛擬函式 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.virtualfunc.override
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8580d27442b0cae7e343a568beaa9aeae500461
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33337739"
---
# <a name="overriding-a-virtual-function-visual-c"></a>覆寫 Virtual 函式 (Visual C++)
您可以從 Visual Studio [屬性視窗](/visualstudio/ide/reference/properties-window)覆寫基底類別中定義的虛擬函式。  
  
### <a name="to-override-a-virtual-function-in-the-properties-window"></a>在 [屬性] 視窗中覆寫虛擬函式  
  
1.  在 [類別檢視] 中，按一下類別。  
  
2.  在 [屬性] 視窗中，按一下 [覆寫] 按鈕。  
  
    > [!NOTE]
    >  當您在 [類別檢視] 中選取類別名稱或按一下原始檔視窗時，即可使用 [覆寫] 按鈕。  
  
     左欄會列出虛擬函式。 如果某個虛擬函式的名稱也出現在右欄，則已實作覆寫。  
  
3.  如果函式沒有覆寫，則按一下 [屬性] 視窗右欄中的儲存格，將函式覆寫的建議名稱顯示為 \<add>*FuncName*。  
  
4.  按一下建議名稱，新增函式的 Stub 程式碼。  
  
5.  若要編輯覆寫函式，請按兩下 [類別檢視] 中的函式名稱，然後在原始檔視窗中編輯程式碼。  
  
 若要移除覆寫，請按一下右欄中的覆寫函式名稱，然後選取 \<delete>*FuncName*。 這會將函式的程式碼標記為註解。  
  
## <a name="see-also"></a>請參閱  
 [使用程式碼精靈新增功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [新增類別](../ide/adding-a-class-visual-cpp.md)   
 [成員函式](../ide/adding-a-member-function-visual-cpp.md)   
 [成員變數](../ide/adding-a-member-variable-visual-cpp.md)   
 [MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../ide/navigating-the-class-structure-visual-cpp.md)