---
title: "可覆寫的 CWinApp 成員函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CWinApp
dev_langs: C++
helpviewer_keywords:
- overriding [MFC], overridable functions in CWinApp
- application class [MFC]
- CWinApp class [MFC], overridables
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64775ad9f44c55529107b50d0695e95e2b9c3a2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="overridable-cwinapp-member-functions"></a>可覆寫的 CWinApp 成員函式
[CWinApp](../mfc/reference/cwinapp-class.md)提供數個索引鍵可覆寫成員函式 (`CWinApp`類別從這些成員會覆寫[CWinThread](../mfc/reference/cwinthread-class.md)，從中`CWinApp`衍生):  
  
-   [InitInstance](../mfc/initinstance-member-function.md)  
  
-   [執行](../mfc/run-member-function.md)  
  
-   [ExitInstance](../mfc/exitinstance-member-function.md)  
  
-   [OnIdle](../mfc/onidle-member-function.md)  
  
 唯一您必須覆寫的 `CWinApp` 成員函式是 `InitInstance`。  
  
## <a name="see-also"></a>請參閱  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)
