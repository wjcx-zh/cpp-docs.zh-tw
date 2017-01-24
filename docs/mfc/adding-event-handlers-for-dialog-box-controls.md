---
title: "Adding Event Handlers for Dialog Box Controls | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "Dialog editor, adding event handlers to controls"
  - "controls [C++], event handlers"
  - "dialog box controls, events"
  - "event handlers, for dialog box controls"
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding Event Handlers for Dialog Box Controls
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

對於與類別關聯的專案對話方塊，當您建立事件處理常式時，您可以利用一些捷徑。  您可以快速地為預設控制項通知事件，或任何適用的 Windows 訊息建立處理常式。  
  
#### 若要建立預設控制項通知事件的處理常式  
  
1.  連按兩次控制項。  文字編輯器隨即開啟。  
  
2.  在文字編輯器中加入控制項通知處理常式碼。  
  
#### 若要為任何適用的 Windows 訊息建立處理常式  
  
1.  請按一下要處理通知事件的控制項。  
  
2.  在[屬性視窗](../Topic/Properties%20Window.md)中，按一下 \[ControlEvents\] 按鈕來顯示與控制項關聯的常見 Windows 事件的清單。  例如，\[關於\] 對話方塊上的標準 \[確定\] 按鈕會列出下列通知事件：  
  
     **BN\_CLICKED**  
  
     **BN\_DOUBLECLICKED**  
  
     **BN\_KILLFOCUS**  
  
     **BN\_SETFOCUS**  
  
    > [!NOTE]
    >  或者，您也可以選取對話方塊，並且按一下 \[ControlEvents\] 按鈕，顯示對話方塊中所有控制項的通用 Windows 事件清單。  
  
3.  在 \[屬性\] 視窗中，按一下要處理之事件旁邊的右欄位，然後選取建議的通知事件名稱 \(例如，**OnBnClickedOK** 處理 **BN\_CLICKED**\)。  
  
    > [!NOTE]
    >  或者，您可以提供您選擇的事件處理常式名稱，而不是選取預設的事件處理常式名稱。  
  
     一旦選取了事件，Visual Studio 會開啟文字編輯器並且顯示事件處理常式的程式碼。  例如，下列程式碼會被加入預設 **OnBnClickedOK**：  
  
    ```  
    void CAboutDlg::OnBnClickedOk(void)  
    {  
       // TODO: Add your control notification handler code here  
    }  
    ```  
  
 如果您要將事件處理常式加入至類別而不是實作對話方塊，請使用[事件處理常式精靈](../ide/event-handler-wizard.md)。  如需詳細資訊，請參閱[加入事件處理常式](../ide/adding-an-event-handler-visual-cpp.md)。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
### 需求  
 Win32  
  
## 請參閱  
 [Default Control Events](../mfc/default-control-events.md)   
 [Defining Member Variables for Dialog Controls](../mfc/defining-member-variables-for-dialog-controls.md)   
 [對話方塊控制項和變數類型](../ide/dialog-box-controls-and-variable-types.md)   
 [加入類別](../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫 Virtual 函式](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 訊息處理常式](../mfc/reference/adding-an-mfc-message-handler.md)