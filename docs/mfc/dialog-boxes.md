---
title: 對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c8de283d81aa9d260b891f285f06555dc67895f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dialog-boxes"></a>對話方塊
Windows 應用程式經常與使用者已透過對話方塊。 類別[CDialog](../mfc/reference/cdialog-class.md)管理對話方塊中，Visual c + + 對話方塊編輯器容易設計對話方塊和建立對話方塊樣板資源，以及程式碼精靈簡化初始化的程序提供的介面和正在驗證的控制項在對話方塊中，並收集使用者輸入的值。  
  
 對話方塊包含控制項，包括：  
  
-   Windows 通用控制項例如編輯方塊、 按鈕、 清單方塊、 下拉式方塊、 樹狀目錄控制項、 清單控制項和進度指標。  
  
-   ActiveX 控制項。  
  
-   為主控描繪控制項： 您必須負責在對話方塊中繪製的控制項。  
  
 大部分對話方塊為強制回應，而這需要使用者關閉對話方塊，然後再使用任何其他部分的程式。 但可以建立非強制回應對話方塊，讓使用者開啟對話方塊時，可與其他 windows。 MFC 支援這兩種類別對話方塊`CDialog`。 控制項的排列和使用對話方塊範本資源，建立與管理[對話方塊編輯器](../windows/dialog-editor.md)。  
  
 [屬性工作表](../mfc/property-sheets-mfc.md)，也稱為索引標籤上的對話方塊，提供了包含 「 頁面 」 不同的對話方塊控制項的對話方塊。 每一頁有檔案資料夾上方的 「 索引標籤 」。 按一下索引標籤對話方塊中的最上層顯示該頁面。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [範例：透過功能表命令顯示對話方塊](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)  
  
-   [架構中的對話方塊元件](../mfc/dialog-box-components-in-the-framework.md)  
  
-   [強制回應和非強制回應對話方塊](../mfc/modal-and-modeless-dialog-boxes.md)  
  
-   [屬性工作表和屬性頁](../mfc/property-sheets-and-property-pages-mfc.md)對話方塊  
  
-   [建立對話方塊資源](../mfc/creating-the-dialog-resource.md)  
  
-   [使用程式碼精靈建立對話方塊類別](../mfc/creating-a-dialog-class-with-code-wizards.md)  
  
-   [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)  
  
-   [對話方塊資料交換 (DDX) 和驗證 (DDV)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [在對話方塊中的控制項類型安全存取](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)  
  
-   [將 Windows 訊息對應到您的類別](../mfc/mapping-windows-messages-to-your-class.md)  
  
-   [常被覆寫的成員函式](../mfc/commonly-overridden-member-functions.md)  
  
-   [常新增的成員函式](../mfc/commonly-added-member-functions.md)  
  
-   [通用對話方塊類別](../mfc/common-dialog-classes.md)  
  
-   [OLE 對話方塊](../mfc/dialog-boxes-in-ole.md)  
  
-   建立應用程式的使用者介面是對話方塊： 請參閱[CMNCTRL1](../visual-cpp-samples.md)或[CMNCTRL2](../visual-cpp-samples.md)範例程式。 應用程式精靈會提供這個選項。  
  
-   [範例](../mfc/dialog-sample-list.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)
