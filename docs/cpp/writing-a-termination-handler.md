---
title: "撰寫終止處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- structured exception handling [C++], termination handlers
- exceptions [C++], terminating
- termination handlers [C++], writing
- handlers [C++]
- handlers [C++], termination
- termination handlers
- exception handling [C++], termination handlers
- try-catch keyword [C++], termination handlers
ms.assetid: 52aa1f8f-f8dd-44b8-be94-5e2fc88d44fb
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b9d4099a7f40acf0b5bfcc89f1c95cb880683b86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="writing-a-termination-handler"></a>撰寫終止處理常式
不同於例外狀況處理常式，無論程式碼保護區塊是否正常終止，都一定會執行終止處理常式。 終止處理常式的唯一用途應該是確保資源 (例如記憶體、控制代碼和檔案) 適當地關閉，而不管程式碼區段的執行如何完成。  
  
 終止處理常式會使用 try-finally 陳述式。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [Try-finally 陳述式](../cpp/try-finally-statement.md)  
  
-   [清除資源](../cpp/cleaning-up-resources.md)  
  
-   [例外狀況處理採取動作的時機](../cpp/timing-of-exception-handling-a-summary.md)  
  
-   [終止處理常式的限制](../cpp/restrictions-on-termination-handlers.md)  
  
## <a name="see-also"></a>請參閱  
 [結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)