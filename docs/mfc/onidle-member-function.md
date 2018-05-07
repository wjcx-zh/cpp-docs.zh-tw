---
title: OnIdle 成員函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnIdle
dev_langs:
- C++
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bbe912db448e424f18b6d72f6e148312c5940687
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="onidle-member-function"></a>OnIdle 成員函式
當正在不處理任何 Windows 訊息時，架構會呼叫[CWinApp](../mfc/reference/cwinapp-class.md)成員函式[OnIdle](../mfc/reference/cwinapp-class.md#onidle) （MFC 程式庫參考中所述）。  
  
 覆寫 `OnIdle` 以執行背景工作。 預設版本會更新使用者介面物件 (例如工具列按鈕) 的狀態，以及執行清除架構在其作業期間建立的暫存物件。 下圖說明沒有訊息在佇列中時，訊息迴圈如何呼叫 `OnIdle`。  
  
 ![訊息迴圈處理序](../mfc/media/vc387c1.gif "vc387c1")  
訊息迴圈  
  
 如需您可以在閒置迴圈中執行的詳細資訊，請參閱[閒置迴圈處理](../mfc/idle-loop-processing.md)。  
  
## <a name="see-also"></a>另請參閱  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)
