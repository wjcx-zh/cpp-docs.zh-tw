---
title: "對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialog 類別, MFC 對話方塊"
  - "MFC 對話方塊"
  - "MFC, 對話方塊"
  - "強制回應對話方塊, MFC 對話方塊"
  - "非強制回應對話方塊, MFC 對話方塊"
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對 Windows 應用程式與使用者經常通訊對話方塊。  [CDialog](../mfc/reference/cdialog-class.md) 類別來管理對話方塊提供的介面， Visual C\+\+ 對話方塊編輯器可讓您輕鬆地設計對話方塊並建立自己的對話方塊範本資源，因此，程式碼精靈可以簡化初始化並驗證在對話方塊的控制流程和收集使用者輸入的值。  
  
 對話方塊包含控制項，包括:  
  
-   Windows 通用控制項 \(例如編輯方塊、按鈕、清單方塊、下拉式方塊、樹狀檢視控制項、清單控制項和進度指示器。  
  
-   ActiveX 控制項。  
  
-   主控描繪控制項:控制項負責在對話方塊的繪圖。  
  
 大部分對話方塊是強制回應對話方塊，要求使用者在使用程式的其他部分之前關閉對話方塊。  但是，建立非強制回應對話方塊，可以讓使用者與其他工具視窗一起使用，當對話方塊開啟時。  MFC 支援兩種類別有 `CDialog`對話方塊。  使用對話方塊範本資源，控制項排列和管理，建立 [對話方塊編輯器](../mfc/dialog-editor.md)。  
  
 [屬性工作表](../mfc/property-sheets-mfc.md)，也稱為選項對話方塊中，為包含「Page」的對話方塊控制項的對話方塊。  每個頁面都有一個資料夾選項」在上面。  按一下選項給對話方塊的最前面該頁面。  
  
## 您還想知道關於哪些方面的詳細資訊？  
  
-   [範例:顯示對話方塊透過功能表命令](../mfc/example-displaying-a-dialog-box-via-a-menu-command.md)  
  
-   [在框架的對話方塊元件](../mfc/dialog-box-components-in-the-framework.md)  
  
-   [強制回應和非強制回應對話方塊](../mfc/modal-and-modeless-dialog-boxes.md)  
  
-   在 對話方塊的[屬性工作表的屬性頁](../mfc/property-sheets-and-property-pages-mfc.md)  
  
-   [建立對話方塊資源](../mfc/creating-the-dialog-resource.md)  
  
-   [建立與程式碼精靈的對話方塊類別。](../mfc/creating-a-dialog-class-with-code-wizards.md)  
  
-   [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)  
  
-   [對話資料交換 \(Dialog Data Exchange，DDX\) 和驗證 \(DDV\)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [對控制項的型別安全存取在對話方塊](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)  
  
-   [對類別的映像的 Windows 訊息。](../mfc/mapping-windows-messages-to-your-class.md)  
  
-   [通常會覆寫的成員函式](../mfc/commonly-overridden-member-functions.md)  
  
-   [通常將成員函式](../mfc/commonly-added-member-functions.md)  
  
-   [通用對話方塊類別](../mfc/common-dialog-classes.md)  
  
-   [在 OLE 的對話方塊](../mfc/dialog-boxes-in-ole.md)  
  
-   建立使用者介面是對話方塊的應用程式:請參閱 [CMNCTRL1](../top/visual-cpp-samples.md) 或 [CMNCTRL2](../top/visual-cpp-samples.md) 範例程式。  應用程式精靈提供這個選項。  
  
-   [範例](../mfc/dialog-sample-list.md)  
  
## 請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)