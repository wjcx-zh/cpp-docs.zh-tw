---
title: "如何： 使用訊息對應交互參考 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: ffa7b39962d78476e971750e92569eb14229606b
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="how-to-use-the-message-map-cross-reference"></a>如何：使用訊息對應交互參考
標示為項目中\<memberFxn >，撰寫您自己的成員函式，針對衍生[CWnd](../../mfc/reference/cwnd-class.md)類別。 您可以自行為函式命名。 其他函式如 `OnActivate`，是 `CWnd` 類別的成員函式。 如果呼叫這些函式，它們就會將訊息傳遞至 `DefWindowProc` Windows 函式。 若要處理 Windows 通知訊息，請覆寫衍生類別中對應的 `CWnd` 函式。 您的函式應該呼叫基底類別中被覆寫的函式，讓基底類別和 Windows 回應訊息。  
  
 在所有情況下，都將函式原型放在 `CWnd`衍生類別標頭，並且撰寫訊息對應項目，如下所示。  
  
 使用下列詞彙:  
  
|詞彙|定義|  
|----------|----------------|  
|id|任何使用者定義的功能表項目 ID (**WM_COMMAND**訊息) 或控制項 ID （子視窗通知訊息）。|  
|「訊息」和「wNotifyCode」|在 WINDOWS.H 定義的 Windows 視窗訊息 ID。|  
|nMessageVariable|包含傳回值的變數名稱**RegisterWindowMessage** Windows 函式。|  
  
## <a name="see-also"></a>另請參閱  
 [訊息對應](../../mfc/reference/message-maps-mfc.md)


