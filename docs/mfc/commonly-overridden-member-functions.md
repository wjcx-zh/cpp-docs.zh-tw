---
title: "常被覆寫的成員函式 | Microsoft Docs"
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
  - "CDialog 類別, 成員"
  - "對話方塊類別, 常被覆寫的成員函式"
  - "MFC 對話方塊, 覆寫成員函式"
  - "OnCancel 函式"
  - "OnInitDialog 函式"
  - "OnOK 函式"
  - "覆寫, 對話方塊類別成員"
ms.assetid: 78eb566c-e361-4c86-8db5-c7e2791b249a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 常被覆寫的成員函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表中的 `CDialog`衍生類別清單很可能覆寫成員函式。  
  
### 通常 CDialog 類別的覆寫成員函式  
  
|成員函式|它的回覆訊息。|覆寫的目的。|  
|----------|-------------|------------|  
|`OnInitDialog`|**WM\_INITDIALOG**|初始化對話方塊的控制項。|  
|`OnOK`|**IDOK**按鈕的 **BN\_CLICKED**|當使用者按一下確定按鈕，請回應。|  
|`OnCancel`|**IDCANCEL** 按鈕的 **BN\_CLICKED**|當使用者按一下取消按鈕，請回應。|  
  
 `OnInitDialog`、 `OnOK`和 `OnCancel` 是虛擬函式。  使用 [屬性視窗](../Topic/Properties%20Window.md)，要覆寫這些屬性，您是在您的衍生對話方塊類別的覆寫函式。  
  
 在對話方塊顯示之前，呼叫`OnInitDialog` 。  您必須呼叫以覆寫的預設 `OnInitDialog` 處理常式 \(通常為處理常式的第一個動作。  根據預設， `OnInitDialog` 會傳回 **TRUE** 表示應該將焦點設定至對話方塊中的第一個控制項。  
  
 `OnOK` 為非強制回應，但不強制回應對話方塊通常會覆寫。  如果您覆寫強制回應對話方塊的這個處理常式，請呼叫以覆寫—確保 `EndDialog` 呼叫或呼叫 `EndDialog` 的基底類別版本。  
  
 `OnCancel` 為非強制回應對話方塊通常會被覆寫。  
  
 如需這些成員函式的詳細資訊，請參閱 [CDialog](../mfc/reference/cdialog-class.md) 類別在 *MFC 參考* 和討論中有關 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)。  
  
## 請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [常加入的成員函式](../mfc/commonly-added-member-functions.md)