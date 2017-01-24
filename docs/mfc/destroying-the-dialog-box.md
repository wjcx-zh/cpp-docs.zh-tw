---
title: "終結對話方塊 | Microsoft Docs"
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
  - "解構, 對話方塊"
  - "對話方塊, 刪除"
  - "對話方塊, 終結"
  - "對話方塊, 移除"
  - "MFC 對話方塊, 終結"
  - "強制回應對話方塊, 終結"
  - "非強制回應對話方塊, 終結"
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 終結對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

強制回應對話方塊時在堆疊框架通常建立和終結以結尾的函式。  當物件超出範圍時，對話方塊物件的解構函式。  
  
 非強制回應對話方塊的父檢視通常會建立和擁有或框架視窗—應用程式的主框架視窗或文件框架視窗。  預設的 [OnClose](../Topic/CWnd::OnClose.md) 處理常式呼叫 [DestroyWindow](../Topic/CWnd::DestroyWindow.md)，終結對話方塊視窗。  如果對話方塊個別代表，所以它或其他特殊擁有權語意的指標，您應該覆寫 [PostNcDestroy](../Topic/CWnd::PostNcDestroy.md) 終結 C\+\+ 對話物件。  您也應該覆寫 [OnCancel](../Topic/CDialog::OnCancel.md) 和呼叫 `DestroyWindow` 從其內部。  當不再需要時，則為，否則為對話方塊的擁有人應終結 C\+\+ 物件。  
  
## 請參閱  
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)