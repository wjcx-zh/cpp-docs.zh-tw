---
title: "混合 C （結構化） 和 c + + 例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 375f954f3df300b50a11067b009614ff8879b9b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mixing-c-structured-and-c-exceptions"></a>混合 C (結構化) 和 C++ 例外狀況
如果您要撰寫更具可攜性的程式碼，不建議您在 C ++ 程式中使用結構化的例外狀況處理。 不過，您有時可能想要使用編譯**/EHa**並混用結構化例外狀況和 c + + 原始程式碼中，而且需要能夠處理這兩種例外狀況。 由於結構化例外狀況處理常式並沒有物件或類型的例外狀況的概念，因此無法處理 c + + 程式碼，所擲回的例外狀況不過，c + +**攔截**處理常式可以處理結構化例外狀況。 為這類，c + + 例外狀況處理語法 (**再試一次**， `throw`，**攔截**) 不接受 C 編譯器，但結構化例外狀況處理語法 (`__try`， `__except`， `__finally`)c + + 編譯器支援。  
  
 請參閱[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)處理為 c + + 例外狀況的結構化例外狀況的資訊。  
  
 如果您混用結構化和 C++ 例外狀況，請注意下列事項：  
  
1.  C++ 例外狀況和結構化例外狀況無法在同一個函式中混用。  
  
2.  即使是在擲回例外狀況之後的回溯期間，終止處理常式 (`__finally` 區塊) 一律會執行。  
  
3.  C + + 例外狀況處理可以攔截並保留回溯語意所編譯的所有模組中[/EH](../build/reference/eh-exception-handling-model.md)編譯器選項 (此選項啟用回溯語意)。  
  
4.  在某些情況下，可能不會針對所有物件呼叫解構函式的函式。 例如，如果嘗試透過未初始化的函式指標進行函式呼叫時發生結構化例外狀況，而且該函式採用呼叫前建構的物件做為參數，則這些物件不會在堆疊回溯期間呼叫其解構函式。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [在 c + + 程式中使用 setjmp 或 longjmp](../cpp/using-setjmp-longjmp.md)  
  
-   [SEH 與 c + + EH 的差異](../cpp/exception-handling-differences.md)  
  
## <a name="see-also"></a>請參閱  
 [C++ 例外狀況處理](../cpp/cpp-exception-handling.md)