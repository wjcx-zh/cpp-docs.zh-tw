---
title: "在對話方塊中使用通用控制項 | Microsoft Docs"
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
  - "通用控制項 [C++], 在對話方塊中"
  - "對話方塊控制項 [C++], 通用控制項"
  - "Windows 通用控制項 [C++], 在對話方塊中"
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在對話方塊中使用通用控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Windows 通用控制項可用於 [對話方塊](../mfc/dialog-boxes.md)，形成檢視、資料錄檢視和根據對話方塊範本的其他視窗。  下列程序，次要變更，為表單上運作。  
  
## 程序  
  
#### 使用公用控制對話方塊  
  
1.  將控制項放在對話方塊範本 [使用對話方塊編輯器](../mfc/using-the-dialog-editor-to-add-controls.md)。  
  
2.  加入至對話方塊類別表示控制項的成員變數。  在 **Add Member Variable** 對話方塊，請檢查 **Control variable** 和 **Control** 確定 **Category**為已選取。  
  
3.  如果這個通用控制項提供輸入至程式，宣告在對話方塊類別的其他成員變數管理這些輸入值。  
  
    > [!NOTE]
    >  您可以加入這些成員變數在類別檢視中使用內容功能表 \(請參閱 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)\)。  
  
4.  在您的對話方塊類別的 [OnInitDialog](../Topic/CDialog::OnInitDialog.md) ，設定通用控制項的初始條件。  使用變數前一步驟所建立的成員，使用成員函式來設定初始值和其他設定。  請參閱下列控制項在設定的詳細資訊的說明。  
  
     您也可以使用 [對話資料交換](../mfc/dialog-data-exchange-and-validation.md) \(Dialog Data Exchange，DDX\) 初始化在對話方塊的控制項。  
  
5.  在對話方塊中控制項的處理常式，使用成員變數操作控制項。  請參閱下列控制項在方法的詳細資訊的說明。  
  
    > [!NOTE]
    >  只有對話方塊存在，成員變數才會存在。  在對話方塊關閉之後，您將無法查詢輸入值的控制項。  要與通用控制項的輸入值時，請覆寫您的對話方塊類別的 `OnOK` 。  在您的覆寫，請查詢輸入值的控制項並儲存這些值在對話方塊類別的成員變數。  
  
    > [!NOTE]
    >  您也可以使用對話資料交換從對話方塊的控制項設定或擷取值。  
  
## 備註  
 一些常見的控制項加入至對話方塊將造成對話方塊不再生效。  參考 [Adding Controls to a Dialog Causes the Dialog to No Longer Function](../mfc/adding-controls-to-a-dialog-causes-the-dialog-to-no-longer-function.md) 有關處理這種情況的詳細資訊。  
  
## 您想要執行甚麼工作？  
  
-   [以手動方式將控制項加入至對話方塊而不是使用對話方塊編輯器](../mfc/adding-controls-by-hand.md)  
  
-   [從其中一個標準 Windows 通用控制項衍生我的控制項](../mfc/deriving-controls-from-a-standard-control.md)  
  
-   [使用通用控制項做為子視窗使用](../mfc/using-a-common-control-as-a-child-window.md)  
  
-   [接收控制項傳回的通知訊息](../mfc/receiving-notification-from-common-controls.md)  
  
-   [使用對話資料交換 \(DDX\)](../mfc/dialog-data-exchange-and-validation.md)  
  
## 請參閱  
 [建立及使用控制項](../mfc/making-and-using-controls.md)   
 [控制項](../mfc/controls-mfc.md)