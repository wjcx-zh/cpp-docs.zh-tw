---
title: "Switching Between Dialog Box Controls and Code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "events [C++], viewing for controls"
  - "Windows messages [C++], controls"
  - "messages [C++], viewing for dialog boxes"
  - "Dialog editor, accessing code"
  - "code [C++], switching from Dialog Editor"
  - "controls [C++], jumping to code"
  - "Dialog editor, switching between controls and code"
ms.assetid: 7da73815-b853-4203-ba45-bbe570695122
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Switching Between Dialog Box Controls and Code
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 MFC 應用程式中，您可以在對話方塊控制項上按兩下跳到它們的處理常式程式碼，或快速地建立 Stub 處理函式。  
  
 選取控制項後，按一下 **ControlEvents** 按鈕或[屬性視窗](../Topic/Properties%20Window.md)中的 \[訊息\] 按鈕來顯示選取項目可以使用的完整 Windows 訊息和事件清單。  從清單選擇要建立或編輯處理函式。  
  
### 若要從對話方塊編輯器移至程式碼  
  
1.  在對話方塊內的控制項上按兩下來移至它的最近實作訊息處理函式的宣告   \(對於 ATL 對話方塊類別，您一定會跳到建構函式 \(Constructor\) 定義\)。  
  
### 若要檢視控制項的事件  
  
1.  選取控制項後，在[屬性視窗](../Topic/Properties%20Window.md)中按一下 \[ControlEvents\] 按鈕。  
  
    > [!NOTE]
    >  當對話方塊有焦點 \(Focus\) 時，按一下 \[ControlEvents\] 按鈕來公開對話方塊中所有控制項的清單，然後您可以展開清單以編輯個別控制項的事件。  
  
     當單一控制項在對話方塊中有焦點時，您可以按一下滑鼠右鍵並且從捷徑功能表選取 \[加入事件處理常式\]。  此步驟能讓您指定加入至處理常式的類別。  如需詳細資訊，請參閱[加入事件處理常式](../ide/adding-an-event-handler-visual-cpp.md)。  
  
### 若要檢視對話方塊的訊息  
  
1.  選取對話方塊後，在[屬性視窗](../Topic/Properties%20Window.md)中按一下 \[訊息\] 按鈕。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [Dialog Editor](../mfc/dialog-editor.md)