---
title: 根據新控制項類別來宣告變數
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.control.variable
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
ms.openlocfilehash: b3b1a168619c1c111db3e71e1a9562d441cc710d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323004"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>根據新控制項類別來宣告變數

當您建立 MFC 控制項類別之後時，您可以宣告變數，以它為基礎。 內容，提供新的變數，您必須開啟對話方塊編輯器，並編輯您要使用的可重複使用控制項的對話方塊。 此外，對話方塊必須已有與其相關聯的類別。 如需使用對話方塊編輯器的詳細資訊，請參閱[對話方塊編輯器](../../windows/dialog-editor.md)。

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>若要宣告變數，根據可重複使用類別

1. 在編輯對話方塊，請從 到對話方塊的 控制項 工具列拖曳相同類型的基底類別的新控制項的控制項。

1. 將滑鼠指標停留在已卸除的控制項。

1. 按住 CTRL 鍵，按兩下控制項。

   [加入成員變數](../../ide/add-member-variable-wizard.md) 對話方塊隨即出現。

1. 在 **存取**方塊中，選取您的控制項的正確存取權。

1. 按一下 **控制變數**核取方塊。

1. 在 **變數的名稱**方塊中，輸入的名稱。

1. 底下**分類**，按一下**控制**。

1. 在 **控制項 ID**清單中，挑選您所加入的控制項。 **變數的型別**清單應該會顯示正確的變數型別，而**控制項類型**方塊應該會顯示正確的控制項型別。

9. 在 **註解**方塊中，新增您想要出現在程式碼中的任何註解。

10. 按一下 [確定] 。

## <a name="see-also"></a>另請參閱

[將訊息對應到函式](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[新增成員函式](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[新增成員變數](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)
