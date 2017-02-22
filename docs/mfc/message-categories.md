---
title: "訊息分類 | Microsoft Docs"
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
  - "命令訊息 [C++]"
  - "控制項通知訊息"
  - "控制項 [MFC], 告知"
  - "訊息處理 [C++], 訊息類型"
  - "訊息 [C++], 分類"
  - "訊息 [C++], Windows"
  - "Windows 訊息 [C++], 分類"
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 訊息分類
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您要為哪些訊息撰寫處理常式?  有三個主要類別：  
  
1.  Windows 訊息  
  
     這個包含從 **WM\_** 前置詞開頭的主要訊息，除了 **WM\_COMMAND**。  Windows 訊息由視窗和檢視處理。  這些訊息通常有用來決定如何處理訊息的參數。  
  
2.  控制通知  
  
     這包括 **WM\_COMMAND** 通知訊息從控制項和其他子視窗至其父視窗。  例如，編輯控制項傳送其父代包含 **EN\_CHANGE** 控制通知程式碼的 **WM\_COMMAND** 訊息，當使用者選擇可能已在編輯器控制項文字的動作時。  訊息的視窗的處理常式回應告知訊息是以適當的方式，例如擷取控制項的文字。  
  
     這個框架傳送像其他 **WM\_** 訊息的控制項告知訊息。  不過，當使用者按一下按鈕時，此按鈕可以傳送一個例外狀況 **BN\_CLICKED** 控制通知資訊。  這個訊息特別視為命令訊息並將像其他命令一樣傳送。  
  
3.  命令訊息  
  
     這包括來自使用者介面物件的 **WM\_COMMAND** 通知訊息：功能表、工具列按鈕和快速鍵。  架構處理命令與其他訊息不同，且可由多個類型物件處理，如 [命令目標](../mfc/command-targets.md)所說明。  
  
##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Windows 訊息和控制通知訊息  
 在型別纜線 1 和 2 的訊息— Windows 訊息和控制通知—由 Windows 處理：從衍生自類別 `CWnd` 的類別的物件 。  這包括 `CFrameWnd`、 `CMDIFrameWnd`、 `CMDIChildWnd`、 `CView`、 `CDialog`，而您自己的類別衍生自這些基底類別。  這類物件封裝 `HWND`，Windows 視窗的控制代碼。  
  
##  <a name="_core_command_messages"></a> 命令訊息  
 在分類 3 的訊息—命令—物件能夠更多種類的處理：文件、文件樣板和應用程式物件的視窗和檢視之外。  當命令直接影響一些特殊物件時，它才會有該物件控制碼命令。  例如，在檔案功能表上的開啟命令在邏輯上與應用程式：應用程式開啟指定的文件在接收命令。  因此開啟命令的處理常式是應用程式類別的成員函式。  如需更多關於命令及其如何傳送至物件，請參閱 [.NET Framework 如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)。  
  
## 請參閱  
 [架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)