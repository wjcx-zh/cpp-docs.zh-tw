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
ms.openlocfilehash: da6a2eca7c2366e519b9bf2e809b042dc3ee2e50
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616863"
---
# <a name="dialog-boxes"></a>對話方塊

適用于 Windows 的應用程式通常會透過對話方塊與使用者通訊。 [類別[CDialog](reference/cdialog-class.md) ] 提供用來管理對話方塊的介面，Visual C++ 對話方塊編輯器可讓您輕鬆地設計對話方塊並建立其對話方塊範本資源，而程式碼嚮導則簡化了初始化和驗證對話方塊中的控制項，以及收集使用者輸入之值的程式。

對話方塊包含控制項，包括：

- Windows 通用控制項，例如編輯方塊、按鈕、清單方塊、下拉式方塊、樹狀控制項、清單控制項和進度指標。

- ActiveX 控制項。

- 主控描繪的控制項：您負責在對話方塊中繪製的控制項。

大部分的對話方塊都是強制回應，這需要使用者先關閉對話方塊，然後再使用程式的任何其他部分。 但是，您可以建立非強制回應對話方塊，讓使用者可以在對話方塊開啟時使用其他視窗。 MFC 支援兩種具有類別的對話方塊 `CDialog` 。 控制項是使用對話方塊[編輯器](../windows/dialog-editor.md)所建立的對話範本資源來排列和管理。

[屬性工作表](property-sheets-mfc.md)（也稱為索引標籤對話方塊）是包含不同對話方塊控制項之「頁面」的對話方塊。 每個頁面頂端都有一個檔案資料夾 "tab"。 按一下索引標籤會將該頁面帶入對話方塊的前方。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [範例：透過功能表命令顯示對話方塊](example-displaying-a-dialog-box-via-a-menu-command.md)

- [架構中的對話方塊元件](dialog-box-components-in-the-framework.md)

- [模式和非強制回應對話方塊](modal-and-modeless-dialog-boxes.md)

- 對話方塊中的[屬性工作表和屬性頁](property-sheets-and-property-pages-mfc.md)

- [建立對話方塊資源](creating-the-dialog-resource.md)

- [使用程式碼嚮導建立對話方塊類別](creating-a-dialog-class-with-code-wizards.md)

- [在 MFC 中使用對話方塊](life-cycle-of-a-dialog-box.md)

- [對話方塊資料交換（DDX）和驗證（DDV）](dialog-data-exchange-and-validation.md)

- [對話方塊中控制項的型別安全存取](type-safe-access-to-controls-in-a-dialog-box.md)

- [將 Windows 訊息對應到您的類別](mapping-windows-messages-to-your-class.md)

- [常被覆寫的成員函式](commonly-overridden-member-functions.md)

- [常新增的成員函式](commonly-added-member-functions.md)

- [通用對話方塊類別](common-dialog-classes.md)

- [OLE 中的對話方塊](dialog-boxes-in-ole.md)

- 建立其使用者介面為對話方塊的應用程式：請參閱[CMNCTRL1](../overview/visual-cpp-samples.md)或[CMNCTRL2](../overview/visual-cpp-samples.md)範例程式。 應用程式精靈也會提供此選項。

- [範例](dialog-sample-list.md)

## <a name="see-also"></a>另請參閱

[使用者介面元素](user-interface-elements-mfc.md)
