---
title: "加入成員變數 （Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.classes.member.variable
dev_langs: C++
helpviewer_keywords:
- member variables, adding
- member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 52d98e3eae6e468db7c2737efac8c2b7ab04abd5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="adding-a-member-variable--visual-c"></a>加入成員變數 (Visual C++)
您可以使用 類別檢視的類別中加入成員變數。 成員變數可以是做為[資料交換和驗證資料](../mfc/dialog-data-exchange-and-validation.md)，也可以是泛型。 資料成員變數精靈是特別設計的相關資訊並使用原始程式檔的適當位置中插入項目。 您可以加入成員變數從[對話方塊編輯器](../windows/dialog-editor.md)中[資源檢視](../windows/resource-view-window.md)，或從[類別檢視](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)。  
  
> [!NOTE]
>  當您設計和實作對話方塊，您可能會發現它更有效率使用對話方塊編輯器加入對話方塊控制項，然後實作控制項的成員變數。  
  
### <a name="to-add-a-member-variable-for-a-dialog-control-in-resource-view-using-the-add-member-variable-wizard"></a>若要使用加入成員變數精靈中的資源檢視中加入對話方塊控制項的成員變數  
  
1.  在資源檢視中，展開專案節點，[對話方塊] 節點來顯示專案的對話方塊中的清單。  
  
2.  按兩下您要加入成員變數，在對話方塊編輯器中開啟的對話方塊。  
  
3.  在對話方塊編輯器中顯示的對話方塊，以滑鼠右鍵按一下您要加入成員變數的控制項。  
  
4.  在捷徑功能表，按一下 **加入變數**顯示[加入成員變數精靈](../ide/add-member-variable-wizard.md)。  
  
    > [!NOTE]
    >  中已提供預設值**控制項 ID**。  
  
5.  提供適當的精靈方塊中的資訊。 請參閱[對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)如需詳細資訊。  
  
6.  按一下**完成**定義和實作程式碼加入專案，並關閉精靈。  
  
### <a name="to-add-a-member-variable-from-class-view-using-the-add-member-variable-wizard"></a>若要加入成員變數，從 類別檢視使用 加入成員變數精靈  
  
1.  在[類別檢視](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，展開專案節點，以顯示專案中的類別。  
  
2.  以滑鼠右鍵按一下您要加入變數的類別。  
  
3.  在捷徑功能表，按一下 **新增**，然後按一下 **加入變數**以顯示 加入成員變數精靈。  
  
4.  提供適當的精靈方塊中的資訊。 請參閱[加入成員變數精靈](../ide/add-member-variable-wizard.md)如需詳細資訊。  
  
5.  按一下**完成**定義和實作程式碼加入專案，並關閉精靈。  
  
## <a name="see-also"></a>請參閱  
 [使用程式碼精靈加入功能](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)   
 [MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../ide/navigating-the-class-structure-visual-cpp.md)