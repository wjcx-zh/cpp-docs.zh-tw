---
title: "終結對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0b1b6c94c4c7efe3bc3300d6c8c5c34fbe890fb4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="destroying-the-dialog-box"></a>終結對話方塊
強制回應對話方塊通常堆疊框架上建立和終結時所建立的函式會結束。 當物件超出範圍時，會呼叫對話方塊物件的解構函式。  
  
 非強制回應對話方塊通常建立和擁有的父檢視或框架視窗，應用程式的主框架視窗或文件框架視窗。 預設值[OnClose](../mfc/reference/cwnd-class.md#onclose)處理常式呼叫[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)，即已遭終結對話方塊視窗。 如果單獨使用沒有指標，或其他特殊的擁有權語意所代表對話方塊中，您應該覆寫[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)終結 c + + 對話方塊物件。 您也應該覆寫[OnCancel](../mfc/reference/cdialog-class.md#oncancel)呼叫`DestroyWindow`從在其中。 如果沒有，不再需要時，對話方塊的擁有者應終結 c + + 物件。  
  
## <a name="see-also"></a>請參閱  
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

