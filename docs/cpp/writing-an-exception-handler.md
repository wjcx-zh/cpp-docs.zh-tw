---
title: "撰寫例外狀況處理常式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], exception handlers
- exception handling [C++], exception handlers
ms.assetid: 71473fee-f773-4a34-bf12-82a3af79579c
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 5f3f81ff6ea954cda7270ff32650d5744280d918
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="writing-an-exception-handler"></a>撰寫例外狀況處理常式
例外狀況處理常式通常用來回應特定錯誤。 除了知道如何處理的項目之外，您可以使用例外狀況處理語法篩選出所有例外狀況。 其他例外狀況應該傳遞給為了尋找這些特定例外狀況所撰寫的其他處理常式 (可能位於執行階段程式庫或作業系統中)。  
  
 例外狀況處理常式會使用 try-except 陳述式。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [再試一次-try-except 陳述式](../cpp/try-except-statement.md)  
  
-   [撰寫例外狀況篩選條件](../cpp/writing-an-exception-filter.md)  
  
-   [引發軟體例外狀況](../cpp/raising-software-exceptions.md)  
  
-   [硬體例外狀況](../cpp/hardware-exceptions.md)  
  
-   [例外狀況處理常式的限制](../cpp/restrictions-on-exception-handlers.md)  
  
## <a name="see-also"></a>另請參閱  
 [結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
