---
title: "樹狀目錄控制項通知訊息 | Microsoft Docs"
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
  - "CTreeCtrl 類別, 告知"
  - "訊息, 告知"
  - "告知, CTreeCtrl"
  - "告知, 樹狀目錄控制項"
  - "樹狀目錄控制項, 通知訊息"
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 樹狀目錄控制項通知訊息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樹狀目錄控制項 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 以 **WM\_NOTIFY** 訊息傳送以下通知訊息:  
  
|通知訊息|說明|  
|----------|--------|  
|**TVN\_BEGINDRAG**|通知拖放作業已開始|  
|**TVN\_BEGINLABELEDIT**|通知啟動就地編輯標籤|  
|**TVN\_BEGINRDRAG**|通知使用滑鼠右鍵，表示拖放作業啟動|  
|**TVN\_DELETEITEM**|表示特定項目的刪除|  
|**TVN\_ENDLABELEDIT**|表示結束編輯標籤|  
|**TVN\_GETDISPINFO**|要求樹狀目錄控制項需要顯示項目的資訊。|  
|**TVN\_ITEMEXPANDED**|通知子項目父項目清單展開或摺疊|  
|**TVN\_ITEMEXPANDING**|通知子項目父項目清單將展開或摺疊|  
|**TVN\_KEYDOWN**|表示鍵盤事件|  
|**TVN\_SELCHANGED**|表示選取項目變更到另一個|  
|**TVN\_SELCHANGING**|表示選取即將變更成另一項目|  
|**TVN\_SETDISPINFO**|更新為項目維持的資訊的通知|  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)