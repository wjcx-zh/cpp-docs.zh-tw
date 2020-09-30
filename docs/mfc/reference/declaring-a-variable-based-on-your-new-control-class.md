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
ms.openlocfilehash: a828351a9e789228143d43d4c0a756abda879989
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506684"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>根據新控制項類別來宣告變數

建立 MFC 控制項類別之後，您就可以根據它來宣告變數。 若要提供新變數的內容，您必須開啟對話方塊編輯器，並編輯您要在其中使用可重複使用之控制項的對話方塊。 此外，對話方塊必須已經有與其相關聯的類別。 如需使用對話方塊編輯器的詳細資訊，請參閱 [對話方塊編輯器](../../windows/dialog-editor.md)。

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>根據可重複使用的類別宣告變數

1. 編輯對話方塊時，請將相同類型的控制項從 [控制項] 工具列中的 [基類] 拖曳至對話方塊。

1. 將滑鼠指標放在拖放的控制項上方。

1. 按下 CTRL 鍵時，按兩下控制項。

   [ [加入成員變數](../../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard) ] 對話方塊隨即出現。

1. 在 [ **存取** ] 方塊中，為您的控制項選取正確的存取權。

1. 按一下 [ **控制項變數** ] 核取方塊。

1. 在 [ **變數名稱** ] 方塊中輸入名稱。

1. 在 [ **類別**] 底下，按一下 [ **控制項**]。

1. 在 [ **控制項識別碼** ] 清單中，選取您加入的控制項。 **變數型**別清單應該會顯示正確的變數型別，而**控制項型**別方塊應該會顯示正確的控制項型別。

1. 在 [ **批註** ] 方塊中，新增您想要在程式碼中顯示的任何批註。

1. 按一下 [確定]。

## <a name="see-also"></a>另請參閱

[將訊息對應至函式](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[新增成員函式](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[新增成員變數](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[巡覽類別結構](../../ide/navigate-code-cpp.md)
