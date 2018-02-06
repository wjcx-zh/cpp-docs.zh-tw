---
title: "處理反映訊息 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c3576e93ce7ce2d972e78433065feaf06f3ae15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="handling-reflected-messages"></a>處理反映訊息
訊息反映可讓您處理訊息的控制項，例如`WM_CTLCOLOR`， **WM_COMMAND**，和**WM_NOTIFY**，控制項本身。 這可讓控制項更具獨立 (Self-Contained) 性及可移植性。 搭配 Windows 通用控制項以及 ActiveX 控制項 (先前稱為 OLE 控制項) 使用的機制。  
  
 訊息反映可讓您更容易地重複使用 `CWnd` 衍生類別。 訊息反映 works 透過[On_xxx_reflect](../mfc/reference/cwnd-class.md#onchildnotify)，使用特殊**ONCHILDNOTIFY**訊息對應項目： 例如， **ON_CTLCOLOR_REFLECT**和**ON_CONTROL_REFLECT**。 [技術提示 62](../mfc/tn062-message-reflection-for-windows-controls.md)說明詳細的訊息反映。  
  
## <a name="what-do-you-want-to-do"></a>您想要做什麼  
  
-   [深入了解訊息反映](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [實作通用控制項的訊息的反映](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [實作 ActiveX 控制項的訊息反映](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)  
  
## <a name="see-also"></a>請參閱  
 [宣告訊息處理函式](../mfc/declaring-message-handler-functions.md)