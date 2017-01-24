---
title: "Adding Controls to a Dialog Causes the Dialog to No Longer Function | Microsoft Docs"
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
  - "C++"
helpviewer_keywords: 
  - "controls [C++], troubleshooting"
  - "common controls, troubleshooting"
  - "troubleshooting controls"
  - "dialog boxes, troubleshooting"
  - "dialog box controls, troubleshooting"
  - "InitCommonControls"
ms.assetid: b2dd4574-ea59-4343-8d65-b387cead5da6
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adding Controls to a Dialog Causes the Dialog to No Longer Function
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將通用控制項或 Rich Edit 控制項加入至對話方塊之後，當您測試對話方塊時，它不會出現或對話方塊本身不會出現。  
  
 **問題範例**  
  
1.  建立 Win32 專案，修改應用程式設定，這樣您可以建立 Windows 應用程式 \(不是主控台應用程式 \(Console Application\)\)。  
  
2.  在[資源檢視](../windows/resource-view-window.md)中，連按兩次 .rc 檔。  
  
3.  在對話方塊選項底下，按兩下 \[關於\] 方塊。  
  
4.  將 \[IP 位址控制項\] 加入至對話方塊。  
  
5.  儲存並且 \[全部重建\]。  
  
6.  執行此程序。  
  
7.  在對話方塊的 \[說明\] 功能表上，按一下 \[關於\] 命令；不會顯示對話方塊。  
  
 **錯誤的原因**  
  
 目前，當您拖放下列通用控制項或 Rich Edit 控制項於對話方塊時，對話方塊編輯器不會自動將程式碼加入您的專案。  當問題發生時，Visual Studio 不會提供錯誤或警告。  您必須手動的加入控制項的程式碼。  
  
||||  
|-|-|-|  
|滑桿控制項|樹狀目錄控制項|日期時間選擇器|  
|微調控制項|索引標籤控制項|月曆|  
|進度控制項|動畫控制項|IP 位址控制項|  
|熱鍵|Rich Edit 控制項|展開的下拉式方塊|  
|清單控制項|Rich Edit 2.0 控制項|自訂控制項|  
  
## 通用控制項的修正  
 為了在對話方塊上使用通用控制項，在您建立對話方塊之前需要呼叫 [InitCommonControlsEx](http://msdn.microsoft.com/library/windows/desktop/bb775697) 或 **AFXInitCommonControls**。  
  
## RichEdit 控制項的修正  
 您必須呼叫 Rich Edit 控制項的 **LoadLibrary**。  如需詳細資訊，請參閱[搭配 MFC 使用 RichEdit 1.0 控制項](../mfc/using-the-richedit-1-0-control-with-mfc.md)、[!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 中的[關於 Rich Edit 控制項](http://msdn.microsoft.com/library/windows/desktop/bb787873)，以及 [Rich Edit 控制項概觀](../mfc/overview-of-the-rich-edit-control.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [Troubleshooting the Dialog Editor](../mfc/troubleshooting-the-dialog-editor.md)   
 [Dialog Editor](../mfc/dialog-editor.md)