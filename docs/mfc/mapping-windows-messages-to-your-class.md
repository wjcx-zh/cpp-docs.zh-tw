---
title: 將 Windows 訊息對應到您的類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 398888a858165197c6e35be791169a9311f3014b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346265"
---
# <a name="mapping-windows-messages-to-your-class"></a>將 Windows 訊息對應到您的類別
如果您需要您的對話方塊，來處理 Windows 訊息時，會覆寫適當的處理常式函式。 若要這樣做，請使用 [屬性] 視窗[對應的訊息](../mfc/reference/mapping-messages-to-functions.md)到對話方塊類別。 此寫入每個訊息的訊息對應項目，並將訊息處理常式成員函式加入至類別。 使用 Visual c + + 原始程式碼編輯器中的訊息處理常式撰寫程式碼。  
  
 您也可以覆寫的成員函式[CDialog](../mfc/reference/cdialog-class.md)和其基底類別，尤其是[CWnd](../mfc/reference/cwnd-class.md)。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [訊息處理和對應](../mfc/message-handling-and-mapping.md)  
  
-   [常被覆寫的成員函式](../mfc/commonly-overridden-member-functions.md)  
  
-   [常加入的成員函式](../mfc/commonly-added-member-functions.md)  
  
## <a name="see-also"></a>另請參閱  
 [對話方塊](../mfc/dialog-boxes.md)   
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

