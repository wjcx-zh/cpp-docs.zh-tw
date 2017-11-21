---
title: "關閉對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d7cd57819c5ab462b0310162d3c043c5f39d2a69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="closing-the-dialog-box"></a>關閉對話方塊
當使用者選擇強制回應對話方塊的任何按鈕 (通常是 [確定] 按鈕或 [取消] 按鈕) 時，對話方塊便會關閉。 選擇 [確定] 或 [取消] 5d; 按鈕會使 Windows 傳送對話方塊物件**BN_CLICKED**和按鈕的控制項通知訊息的識別碼，或是**IDOK**或**IDCANCEL**。 `CDialog` 會為以下訊息提供預設的處理函式：`OnOK` 和 `OnCancel`。 預設處理常式會呼叫 `EndDialog` 成員函式，以關閉對話方塊視窗。 您也可以從自己的程式碼呼叫 `EndDialog`。 如需詳細資訊，請參閱[EndDialog](../mfc/reference/cdialog-class.md#enddialog)類別成員函式`CDialog`中*MFC 參考*。  
  
 若要安排關閉和刪除非強制回應對話方塊，覆寫`PostNcDestroy`和叫用**刪除**運算子**這**指標。 [終結對話方塊](../mfc/destroying-the-dialog-box.md)說明接下來的情況。  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

