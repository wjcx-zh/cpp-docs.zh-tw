---
title: 新的控制項類別宣告變數根據 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.classes.control.variable
dev_langs:
- C++
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 677006d441c940f478b3d23744d1057667307e1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370610"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>根據新控制項類別來宣告變數
當您建立 MFC 控制項類別之後時，您可以宣告變數，它為基礎。 若要提供新的變數的內容，您必須開啟對話方塊編輯器，並編輯您要重複使用控制項的對話方塊。 此外，對話方塊中，必須已有與其相關聯的類別。 如需使用對話方塊編輯器中的資訊，請參閱[對話方塊編輯器](../../windows/dialog-editor.md)。  
  
### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>宣告變數根據可重複使用的類別  
  
1.  在編輯時對話方塊中，拖曳到對話方塊的 [控制項] 工具列中的相同類型的基底類別的新控制項的控制項。  
  
2.  將滑鼠指標移至已卸除的控制項。  
  
3.  按住 CTRL 鍵，在控制項上按兩下。  
  
     [加入成員變數](../../ide/add-member-variable-wizard.md) 對話方塊隨即出現。  
  
4.  在**存取**方塊中，選取您的控制項的正確存取權。  
  
5.  按一下**控制變數**核取方塊。  
  
6.  在**變數名稱**方塊中輸入名稱。  
  
7.  在下**類別**，按一下 **控制項**。  
  
8.  在**控制項 ID**清單中，選取您加入的控制項。 **變數型別**清單應該會顯示正確的變數型別，而**控制項類型**方塊應該顯示正確的控制項類型。  
  
9. 在**註解**方塊中，加入任何您想要出現在程式碼中的註解。  
  
10. 按一下 [確定 **Deploying Office Solutions**]。  
  
## <a name="see-also"></a>另請參閱  
 [將訊息對應到函式](../../mfc/reference/mapping-messages-to-functions.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)
