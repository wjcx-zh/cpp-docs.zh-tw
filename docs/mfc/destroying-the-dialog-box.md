---
title: 終結對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66a3ef9a72107ffb36a75834a6e197aba394c420
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="destroying-the-dialog-box"></a>終結對話方塊
強制回應對話方塊通常堆疊框架上建立和終結時所建立的函式會結束。 當物件超出範圍時，會呼叫對話方塊物件的解構函式。  
  
 非強制回應對話方塊通常建立和擁有的父檢視或框架視窗，應用程式的主框架視窗或文件框架視窗。 預設值[OnClose](../mfc/reference/cwnd-class.md#onclose)處理常式呼叫[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)，即已遭終結對話方塊視窗。 如果單獨使用沒有指標，或其他特殊的擁有權語意所代表對話方塊中，您應該覆寫[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)終結 c + + 對話方塊物件。 您也應該覆寫[OnCancel](../mfc/reference/cdialog-class.md#oncancel)呼叫`DestroyWindow`從在其中。 如果沒有，不再需要時，對話方塊的擁有者應終結 c + + 物件。  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

