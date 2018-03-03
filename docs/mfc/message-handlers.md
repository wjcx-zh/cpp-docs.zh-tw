---
title: "訊息處理常式 |Microsoft 文件"
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
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d1b906a49d7da7ed8505252a1759d7ea00fcda1f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="message-handlers"></a>訊息處理常式
在 MFC 中，專用*處理常式*函式會處理每個個別的訊息。 訊息處理函式是類別的成員函式。 本文件使用條款*訊息處理常式成員函式*，*訊息處理常式函式*，*訊息處理常式*，和*處理常式*交換使用。 有些類型的訊息處理常式也稱為「命令處理常式」。  
  
 撰寫訊息處理常式在架構應用程式的撰寫中佔相當大的比例。 本文章系列說明訊息處理機制的運作方式。  
  
 用途這樣的訊息處理常式沒有您想要在回應訊息。 您可以使用類別的 [屬性] 視窗建立處理常式，然後使用原始程式碼編輯器填入處理常式的程式碼。  
  
 您可以使用任何 Microsoft Visual C++ 和 MFC 的功能撰寫處理常式。 如需所有類別的清單，請參閱[類別庫概觀](../mfc/class-library-overview.md)中*MFC 參考*。  
  
## <a name="see-also"></a>請參閱  
 [架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)

