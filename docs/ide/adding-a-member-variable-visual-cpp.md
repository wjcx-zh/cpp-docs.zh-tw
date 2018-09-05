---
title: 新增成員變數 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.classes.member.variable
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding
- member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dade9987358c1c160dffd0221b0421b4fab92c24
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687638"
---
# <a name="adding-a-member-variable--visual-c"></a>加入成員變數 (Visual C++)
您可以使用 [類別檢視] 將成員變數新增至類別。 成員變數可以是用於[資料交換和資料驗證](../mfc/dialog-data-exchange-and-validation.md)，也可以是泛型。 資料成員變數精靈是特別設計來取得相關資訊並用來在原始程式檔的適當位置插入項目。 您可以從[資源檢視](../windows/resource-view-window.md)中的[對話方塊編輯器](../windows/dialog-editor.md)，或從[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)新增成員變數。  
  
> [!NOTE]
>  當您設計和實作對話方塊時，可能會發現使用對話方塊編輯器新增對話方塊控制項，然後實作控制項的成員變數這樣的做法更有效率。  
  
### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>使用 [新增成員變數精靈] 中的 [資源檢視] 新增對話方塊控制項的成員變數  
  
1.  在 [資源檢視] 中，展開專案節點及對話方塊節點，顯示專案的對話方塊清單。  
  
2.  按兩下您要新增成員變數的對話方塊，在對話方塊編輯器中開啟它。  
  
3.  在對話方塊編輯器中顯示的對話方塊中，以滑鼠右鍵按一下您要新增成員變數的控制項。  
  
4.  在捷徑功能表上，按一下 [新增變數]，顯示[新增成員變數精靈](../ide/add-member-variable-wizard.md)。  
  
    > [!NOTE]
    >  [控制項識別碼] 中已提供預設值。  
  
5.  在適當的精靈方塊中提供資訊。 如需詳細資訊，請參閱[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)。  
  
6.  按一下 [完成]，將定義和實作程式碼新增至專案，然後關閉精靈。  
  
### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>使用 [新增成員變數精靈] 從 [類別檢視] 新增成員變數  
  
1.  在[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)中，展開專案節點，顯示專案中的類別。  
  
2.  以滑鼠右鍵按一下您要新增變數的類別。  
  
3.  在捷徑功能表上，依序按一下 [新增]、[新增變數]，顯示 [新增成員變數精靈]。  
  
4.  在適當的精靈方塊中提供資訊。 如需詳細資料，請參閱[新增成員變數精靈](../ide/add-member-variable-wizard.md)。  
  
5.  按一下 [完成]，將定義和實作程式碼新增至專案，然後關閉精靈。  
  
## <a name="see-also"></a>請參閱  
 [使用程式碼精靈新增功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [新增類別](../ide/adding-a-class-visual-cpp.md)   
 [成員函式](../ide/adding-a-member-function-visual-cpp.md)   
 [MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../ide/navigating-the-class-structure-visual-cpp.md)