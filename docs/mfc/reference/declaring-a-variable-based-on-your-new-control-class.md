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
ms.openlocfilehash: 994f81524001a80d1cf0dd3783b9de742d61e84d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365850"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>根據新控制項類別來宣告變數

創建 MFC 控制類後,可以基於它聲明變數。 要為新變數提供上下文,必須打開對話框編輯器並編輯要在其中使用可重用控制項的對話方塊。 此外,對話框必須已具有與其關聯的類。 有關使用對話框編輯器的資訊,請參考[對話框編輯器](../../windows/dialog-editor.md)。

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>基於可重用類別聲明變數

1. 編輯對話方塊時,將與新控制項的基類相同的控制項從「控制件」工具列拖動到對話框中。

1. 將滑鼠指標放在丟棄的控制項上。

1. 按下 CTRL 鍵時,按兩下控制項。

   將顯示「[新增成員變數」](../../ide/add-member-variable-wizard.md)對話框。

1. 在 **「訪問」** 框中,為控制項選擇正確的訪問。

1. 按下 **「控制變數**」複選框。

1. 在 **"變數名稱"** 框中,鍵入名稱。

1. 在**類別**下,單擊 **"控制**"。

1. 在 **「控制項識別代碼」** 清單中,選擇新增的控制項。 **變數類型**清單應顯示正確的變數類型,**控制項類型**框應顯示正確的控制項類型。

1. 在 **「註釋」** 框中,添加要在代碼中顯示的任何註釋。

1. 按一下 [確定]  。

## <a name="see-also"></a>另請參閱

[將訊息對應到函式](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[使用程式碼精靈新增功能](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[新增類別](../../ide/adding-a-class-visual-cpp.md)<br/>
[新增成員函式](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[新增成員變數](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[巡覽類別結構](../../ide/navigate-code-cpp.md)
