---
title: "與使用者介面物件關聯的訊息類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.uiobject.msgs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "訊息類型和使用者介面物件"
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 與使用者介面物件關聯的訊息類型
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下表顯示使用的物件型別，以及與物件型別關聯的訊息類型。  
  
### 使用者介面物件和關聯的訊息  
  
|物件 ID|訊息|  
|-----------|--------|  
|類別名稱，表示所包含的視窗|Windows 訊息，適合下列 [CWnd](../../mfc/reference/cwnd-class.md) 衍生類別：對話方塊、視窗、子視窗、MDI 子視窗或最上層框架視窗。|  
|功能表或快速鍵 \(Accelerator\) 識別項|-   **COMMAND** 訊息 \(執行程式函式\)<br />-   **UPDATE\_COMMAND\_UI** 訊息 \(動態更新功能表項目\)|  
|控制識別項 \(Control Identifier\)|所選控制項型別的控制項告知訊息。|  
  
## 請參閱  
 [將訊息對應到函式](../../mfc/reference/mapping-messages-to-functions.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫 Virtual 函式](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)