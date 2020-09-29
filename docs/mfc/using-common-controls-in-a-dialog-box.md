---
title: 在對話方塊中使用通用控制項
ms.date: 11/04/2016
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- dialog box controls [MFC], common controls
- Windows common controls [MFC], in dialog boxes
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
ms.openlocfilehash: 1a3dcb7151952b52affcfeb838ced15f0d116fce
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500351"
---
# <a name="using-common-controls-in-a-dialog-box"></a>在對話方塊中使用通用控制項

Windows 通用控制項可用於 [對話方塊](../mfc/dialog-boxes.md)、表單檢視、記錄視圖，以及根據對話方塊範本的其他任何視窗。 下列含次要變更的程序，也可處理表單。

## <a name="procedures"></a>程序

#### <a name="to-use-a-common-control-in-a-dialog-box"></a>在對話方塊中使用通用控制

1. [使用對話方塊編輯器](../mfc/using-the-dialog-editor-to-add-controls.md)將控制項放在對話方塊範本上。

1. 將表示控制項的成員變數加入對話方塊類別。 在 [**加入成員變數**] 對話方塊中，核取 [**控制變數**]，並確定已針對 [**類別目錄**] 選取 [**控制項**]。

1. 如果這個通用控制項提供輸入到程式中，請在對話方塊類別宣告其他成員變數，以處理這些輸入值。

    > [!NOTE]
    >  您可以使用類別檢視中的內容功能表來新增這些成員變數 (請參閱 [新增成員變數](../ide/adding-a-member-variable-visual-cpp.md)) 。

1. 在對話方塊類別的 [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) 中，設定通用控制項的初始條件。 使用前一步驟所建立的成員變數，使用成員函式設定初始值和其他設定值。 如需有關設定值的詳細資訊，請參閱下列控制項的描述。

   您也可以使用 [對話方塊資料交換](../mfc/dialog-data-exchange-and-validation.md) (DDX) 來初始化對話方塊中的控制項。

1. 在對話方塊的控制項處理常式，使用成員變數操作控制項。 如需有關方法的詳細資訊，請參閱下列控制項的說明描述。

    > [!NOTE]
    >  只有對話方塊存在，成員變數才會存在。 在關閉對話方塊之後，您將無法查詢輸入值的控制項。 若要使用通用控制項的輸入值，請覆寫您的對話方塊類別的 `OnOK`。 在您的覆寫中查詢輸入值的控制項，並將這些值儲存在對話方塊類別的成員變數中。

    > [!NOTE]
    >  您也可以使用對話方塊資料交換，設定或擷取對話方塊控制項的值。

## <a name="remarks"></a>備註

在對話方塊加入一些通用控制項將造成對話方塊無法再運作。 請參閱 [將控制項新增至對話方塊，讓對話方塊不再](../windows/adding-editing-or-deleting-controls.md) 有關于處理這種情況的詳細資訊。

## <a name="what-do-you-want-to-do"></a>您要做什麼

- [以手動方式將控制項加入至對話方塊而不是使用對話方塊編輯器](../mfc/adding-controls-by-hand.md)

- [從其中一個標準 Windows 通用控制項衍生我的控制項](../mfc/deriving-controls-from-a-standard-control.md)

- [使用通用控制項當做子視窗](../mfc/using-a-common-control-as-a-child-window.md)

- [接收控制項的通知訊息](../mfc/receiving-notification-from-common-controls.md)

- [使用對話方塊資料交換 (DDX)](../mfc/dialog-data-exchange-and-validation.md)

## <a name="see-also"></a>另請參閱

[建立和使用控制項](../mfc/making-and-using-controls.md)<br/>
[控制項](../mfc/controls-mfc.md)
