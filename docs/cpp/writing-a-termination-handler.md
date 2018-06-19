---
title: 撰寫終止處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d37319e50e7d2429ca9b64c5fc81d8c7c4418ed5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423232"
---
# <a name="writing-a-termination-handler"></a>撰寫終止處理常式
不同於例外狀況處理常式，無論程式碼保護區塊是否正常終止，都一定會執行終止處理常式。 終止處理常式的唯一用途應該是確保資源 (例如記憶體、控制代碼和檔案) 適當地關閉，而不管程式碼區段的執行如何完成。  
  
 終止處理常式會使用 try-finally 陳述式。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [Try-finally 陳述式](../cpp/try-finally-statement.md)  
  
-   [清除資源](../cpp/cleaning-up-resources.md)  
  
-   [例外狀況處理採取動作的時機](../cpp/timing-of-exception-handling-a-summary.md)  
  
-   [終止處理常式的限制](../cpp/restrictions-on-termination-handlers.md)  
  
## <a name="see-also"></a>另請參閱  
 [結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)