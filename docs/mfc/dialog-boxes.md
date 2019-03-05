---
title: 對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
ms.openlocfilehash: 9add6f003f0f6cd4ab85980e1e35370770da43aa
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282054"
---
# <a name="dialog-boxes"></a>對話方塊

與透過對話方塊使用者經常通訊的 Windows 應用程式。 類別[CDialog](../mfc/reference/cdialog-class.md)提供用來管理對話方塊時，Visual c + + 對話方塊編輯器中輕鬆地設計對話方塊，並建立其對話方塊範本資源，以及程式碼精靈可以簡化程序初始化介面和正在驗證的控制項在對話方塊中，並收集使用者輸入的值。

對話方塊包含的控制項，包括：

- Windows 通用控制項這類編輯方塊、 按鈕、 清單方塊、 下拉式方塊、 樹狀目錄控制項、 清單控制項和進度指標。

- ActiveX 控制項。

- 為主控描繪控制項： 您必須負責繪製在對話方塊中的控制項。

大多數對話方塊是強制回應，這會要求使用者使用該程式的任何其他部分之前關閉對話方塊。 但是，就可以建立非強制回應對話方塊，讓使用者可與其他視窗 對話方塊開啟時。 MFC 支援這兩種類別的對話方塊`CDialog`。 這些控制項的排列，而且使用對話方塊範本資源，以建立管理[對話方塊編輯器](../windows/dialog-editor.md)。

[屬性工作表](../mfc/property-sheets-mfc.md)，也稱為索引標籤上的對話方塊，會包含 「 頁面 」 不同的對話方塊控制項的對話方塊。 每個頁面具有 「 索引標籤頂端中的 [檔案] 資料夾。 按一下 索引標籤對話方塊中的最上層叫該頁面。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [例如：顯示對話方塊，透過功能表命令](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)

- [架構中的對話方塊元件](../mfc/dialog-box-components-in-the-framework.md)

- [強制回應和非強制回應對話方塊](../mfc/modal-and-modeless-dialog-boxes.md)

- [屬性工作表和屬性頁](../mfc/property-sheets-and-property-pages-mfc.md)在對話方塊中

- [建立對話方塊資源](../mfc/creating-the-dialog-resource.md)

- [使用程式碼精靈建立對話方塊類別](../mfc/creating-a-dialog-class-with-code-wizards.md)

- [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

- [對話方塊資料交換 (DDX) 和驗證 (DDV)](../mfc/dialog-data-exchange-and-validation.md)

- [在對話方塊中的控制項型別安全存取](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)

- [將 Windows 訊息對應到您的類別](../mfc/mapping-windows-messages-to-your-class.md)

- [常被覆寫的成員函式](../mfc/commonly-overridden-member-functions.md)

- [常新增的成員函式](../mfc/commonly-added-member-functions.md)

- [通用對話方塊類別](../mfc/common-dialog-classes.md)

- [在 OLE 中的對話方塊](../mfc/dialog-boxes-in-ole.md)

- 建立應用程式的使用者介面是對話方塊： 請參閱[CMNCTRL1](../visual-cpp-samples.md)或是[CMNCTRL2](../visual-cpp-samples.md)範例程式。 應用程式精靈 會提供此選項。

- [範例](../mfc/dialog-sample-list.md)

## <a name="see-also"></a>另請參閱

[使用者介面項目](../mfc/user-interface-elements-mfc.md)
