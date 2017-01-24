---
title: "以手動方式加入控制項 | Microsoft Docs"
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
  - "通用控制項 [C++], 加入"
  - "控制輸入焦點"
  - "控制項 [MFC], 加入至對話方塊"
  - "對話方塊控制項 [C++], 加入至對話方塊"
  - "焦點, 控制輸入"
  - "輸入焦點控制"
  - "Windows 通用控制項 [C++], 加入"
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 以手動方式加入控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以 [將控制項加入對話方塊編輯器的對話方塊。](../mfc/using-the-dialog-editor-to-add-controls.md) 或將它們，有程式碼的。  
  
 若要建立控制項物件，您可以在 C \+\+. 對話方塊或框架視窗物件通常會內嵌 C\+\+ 主控物件。  與這個框架的許多其他物件，則控制項需要兩階段建構。  為建立父對話方塊或框架視窗的一部分，您應該呼叫控制項的 **Create** 成員函式。  對於對話方塊，這通常是在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)和為框架視窗，以 [OnCreate](../Topic/CWnd::OnCreate.md)為單位。  
  
 下列範例顯示要宣告在衍生的對話方塊類別的類別宣告的 `CEdit` 物件會呼叫 `OnInitDialog`**Create** 的成員函式。  由於 `CEdit` 物件宣告為內嵌物件，它會自動建構，該對話方塊建構物件時，不過，仍然必須將它初始化其 **Create** 成員函式。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/CPP/adding-controls-by-hand_1.h)]  
  
 下列 `OnInitDialog` 函式會設定矩形，然後呼叫 **Create** 建立 Windows 編輯控制項並將它附加至未初始化的 `CEdit` 物件。  
  
 [!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/CPP/adding-controls-by-hand_2.cpp)]  
  
 在建立編輯物件之後，您還可以將輸入焦點移至控制項呼叫 `SetFocus` 成員函式。  最後，您會從 0 表示 `OnInitDialog` ，可以設定焦點。  如果您傳回非零值，對話方塊管理員將焦點設定在對話方塊中的項目清單中的第一個控制項項目。  在大部分情況下，您會想要將控制項加入至具有對話方塊編輯器的對話方塊。  
  
## 請參閱  
 [建立及使用控制項](../mfc/making-and-using-controls.md)   
 [控制項](../mfc/controls-mfc.md)   
 [CDialog::OnInitDialog](../Topic/CDialog::OnInitDialog.md)