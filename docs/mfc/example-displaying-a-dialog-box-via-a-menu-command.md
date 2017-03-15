---
title: "範例：透過功能表命令顯示對話方塊 | Microsoft Docs"
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
  - "對話方塊, MFC"
  - "範例 [MFC], 對話方塊"
  - "功能表項目, 範例"
  - "MFC 對話方塊, 顯示"
  - "MFC 對話方塊, 範例"
  - "強制回應對話方塊, 顯示"
  - "非強制回應對話方塊, 顯示"
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 範例：透過功能表命令顯示對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題包含程序:  
  
-   透過功能表命令顯示強制回應對話方塊。  
  
-   透過功能表命令顯示非強制回應對話方塊。  
  
 兩個範例程序是為 MFC 應用程式，並會在您使用 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)建立的應用程式。  
  
 使用下列程序名稱和值:  
  
|項目|名稱或值。|  
|--------|-----------|  
|應用程式|DisplayDialog|  
|功能表命令|在檢視\] 功能表的測試命令;命令 ID \= ID\_VIEW\_TEST|  
|對話方塊|測試對話方塊;類別 CTestDialog \=;標頭檔 \= TestDialog.h;變數 \= testdlg， ptestdlg|  
|命令處理常式|OnViewTest|  
  
### 顯示強制回應對話方塊  
  
1.  建立功能表命令;請參閱 [建立功能表或功能表項目](../windows/creating-a-menu.md)。  
  
2.  建立對話方塊;請參閱 [開啟對話方塊編輯器](../mfc/creating-a-new-dialog-box.md)。  
  
3.  將對話方塊的類別。  請參閱 [加入類別](../ide/adding-a-class-visual-cpp.md) 以取得詳細資訊。  
  
4.  在 \[**類別檢視**\] 中，選取文件類別 \(CDisplayDialogDoc\)。  在 \[**屬性**\] 視窗中，按一下 **Events** 按鈕。  按兩下命令 \(ID\_VIEW\_TEST\) 的 ID 在 \[**屬性**\] 視窗的左窗格中選擇 **Command**。  在右窗格中，按一下向下箭號並選取 **\<Add\> OnViewTest**。  
  
     如果您已將命令加入至 MDI 應用程式的電腦主機，請選取應用程式類別 \(CDisplayDialogApp\)。  
  
5.  將包含下列陳述式加入至 CDisplayDialogDoc.cpp \(或 CDisplayDialogApp.cpp\) 在現有包含陳述式之後:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
6.  將下列程式碼新增至 `OnViewTest` 實作函式:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#43](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_2.cpp)]  
  
### 顯示非強制回應對話方塊  
  
1.  執行前四個步驟顯示強制回應對話方塊，不過，選取檢視類別 \(CDisplayDialogView\) 在第 4. 步驟。  
  
2.  編輯 DisplayDialogView.h:  
  
    -   宣告在第一個類別宣告之前的對話方塊類別:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#44](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_3.h)]  
  
    -   宣告指標到對話方塊在屬性公開部分之後:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#45](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_4.h)]  
  
3.  編輯 DisplayDialogView.cpp:  
  
    -   在現有的 Include 陳述式之後加入下列包含陳述式:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
    -   將下列程式碼加入至建構函式:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#46](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_5.cpp)]  
  
    -   將下列程式碼加入至解構函式:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#47](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_6.cpp)]  
  
    -   將下列程式碼新增至 `OnViewTest` 實作函式:  
  
         [!code-cpp[NVC_MFCControlLadenDialog#48](../mfc/codesnippet/CPP/example-displaying-a-dialog-box-via-a-menu-command_7.cpp)]  
  
 此外，請參閱下列知識庫 \(Knowledge Base\) 文件:  
  
-   Q251059:HOWTO:提供 MFC 對話方塊中提供自己的視窗類別名稱。  
  
## 請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [強制回應和非強制回應對話方塊](../mfc/modal-and-modeless-dialog-boxes.md)