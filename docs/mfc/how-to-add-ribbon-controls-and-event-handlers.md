---
title: "如何：加入功能區控制項和事件處理常式 | Microsoft Docs"
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
  - "事件處理常式, 加入"
  - "功能區控制項, 加入"
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：加入功能區控制項和事件處理常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

功能區控制項項目，例如按鈕和下拉式方塊，那您新增至面板。  面板是顯示相關控制項群組功能區列的區域。  
  
 本主題中，您會開啟功能區設計工具，將按鈕，然後連接顯示「Hello World」的事件。  
  
### 開啟功能區設計工具  
  
1.  在 Visual Studio 中，按一下 \[**檢視**\] 功能表上，按一下 \[**資源檢視**\]。  
  
2.  在 \[**資源檢視**\] 中，按兩下功能區資源顯示在設計介面上。  
  
### 將按鈕和事件處理常式  
  
1.  從 \[**工具列**\] 中，按一下 \[**按鈕**\] 並將其拖曳到設計介面上的面板。  
  
2.  以滑鼠右鍵按一下按鈕，然後按一下 \[ **加入事件處理常式**\]。  
  
3.  在 \[**事件處理常式精靈。**\] 中，確認預設值並按一下 \[**加入和編輯**\]。  如需詳細資訊，請參閱[事件處理常式精靈](../ide/event-handler-wizard.md)。  
  
4.  在程式碼編輯器中，加入下列程式碼輸入到處理常式函式:  
  
    ```  
    MessageBox((LPCTSTR)L"Hello World");  
    ```  
  
## 請參閱  
 [RibbonGadgets 範例：功能區小工具應用程式](../top/visual-cpp-samples.md)   
 [功能區設計工具 \(MFC\)](../mfc/ribbon-designer-mfc.md)