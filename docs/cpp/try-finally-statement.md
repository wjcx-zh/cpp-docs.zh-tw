---
title: "try-finally 陳述式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
dev_langs:
- C++
helpviewer_keywords:
- __try keyword [C++]
- __finally keyword [C++]
- __leave keyword [C++]
- try-catch keyword [C++], try-finally keyword
- try-finally keyword [C++]
- __finally keyword [C++], try-finally statement syntax
- __leave keyword [C++], try-finally statement
- structured exception handling, try-finally
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 5bfaa7d2a2f75fa479f135a61c15f9fcf3bbf5ca
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="try-finally-statement"></a>try-finally 陳述式
**Microsoft 特定的**  
  
 下列語法描述 `try-finally` 陳述式：  
  
```  
__try {  
   // guarded code  
}  
__finally {  
   // termination code  
}  
```  
  
## <a name="grammar"></a>文法  
 *try-finally-statement*：  
 `__try`*複合陳述式*  
  
 `__finally`*複合陳述式*  
  
 `try-finally` 陳述式是 C 和 C++ 語言的 Microsoft 擴充功能，可讓目標應用程式在執行程式碼的區塊中斷時，仍可保證會執行清除程式碼。 清除包含如取消配置記憶體、關閉檔案和釋放檔案控制代碼等工作。 `try-finally` 陳述式對於有多個地方要檢查可能會導致常式過早傳回的錯誤時會特別有用。  
  
 如需相關的資訊和程式碼範例，請參閱[再試一次-try-except 陳述式](../cpp/try-except-statement.md)。 如需結構化例外狀況處理的詳細資訊，請參閱[結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)。 如需有關受管理的應用程式中處理例外狀況的詳細資訊，請參閱[/clr 底下處理時發生例外狀況](../windows/exception-handling-cpp-component-extensions.md)。  
  
> [!NOTE]
>  結構化例外狀況處理可搭配 Win32 處理 C 和 C++ 原始程式檔。 不過，它不是專為 C++ 所設計。 使用 C++ 例外狀況處理可確保您的程式碼更具可移植性。 此外，C++ 例外狀況處理更有彈性，因為它可以處理任何類型的例外狀況。 對於 c + + 程式，建議您使用 c + + 例外狀況處理機制 ([try、 catch 和 throw](../cpp/try-throw-and-catch-statements-cpp.md)陳述式)。  
  
 `__try` 子句後面的複合陳述式是保護的區段。 `__finally` 子句後面的複合陳述式則是終止處理常式。 處理常式會指定一組當保護區段結束時執行的動作，不管保護的區段是因例外狀況 (異常終止) 而結束，或是依標準的執行順序 (正常終止) 而結束。  
  
 此時控制項會經由簡單的循序執行 (正常執行) 到達 `__try` 陳述式。 當控制項進入 `__try` 時，與其關聯的處理常式會變成作用中。 如果控制流程到達 try 區塊的結尾，執行程序如下所示：  
  
1.  已叫用終止處理常式。  
  
2.  當終止處理常式完成時，便會從 `__finally` 陳述式之後繼續執行。 不論保護的區段如何結束 (例如，藉由保護主體外部的 `goto` 或是經由 `return` 陳述式)，終止處理常式會在控制流程移出保護區段 `before` 之前執行。  
  
     A **__finally**陳述式不會封鎖搜尋適當的例外狀況處理常式。  
  
 如果在 `__try` 區塊中發生例外狀況，作業系統必須尋找例外狀況的處理常式，否則程式將會失敗。 如果找到處理常式，將會執行任何及所有 `__finally` 區塊，並且在處理常式中繼續執行。  
  
 例如，假設有一系列的函式呼叫連結了函式 A 與函式 D，如下圖所示。 每個函式都具有一個終止處理常式。 如果例外狀況在函式 D 中引發，並在函式 A 中處理，則會在系統回溯堆疊時，依此順序呼叫終止處理常式：D、C、B。  
  
 ![終止 & #45 順序，則處理常式執行](../cpp/media/vc38cx1.gif "vc38CX1")  
終止處理常式的執行順序  
  
> [!NOTE]
>  Try-finally 的行為是不同於其他語言支援使用**最後**，例如 C#。  單一 `__try` 可能具有其中一個 (但並非兩者) `__finally` 和 `__except`。  如果要同時使用兩個，外層的 try-except 陳述式必須以引號括住內部 try-finally 陳述式。  指定的規則在每個區塊執行時也不同。  
  
## <a name="the-leave-keyword"></a>__leave 關鍵字  
 `__leave` 關鍵字只有在 `try-finally` 陳述式的保護區段內才有效，而其作用是跳至保護區段的結尾。 然後從終止處理常式中的第一個陳述式繼續執行。  
  
 `goto` 陳述式也可以跳出保護的區段，但不會降低效能，因為它不會導致堆疊回溯。 由於 `__leave` 陳述式不會導致堆疊回溯，因此會更有效率。  
  
## <a name="abnormal-termination"></a>異常終止  
 結束`try-finally`陳述式使用[longjmp](../c-runtime-library/reference/longjmp.md)執行階段函式會視為是異常終止。 雖然不可跳入 `__try` 陳述式，但是可以從這類陳述式跳出。 起點 (`__finally` 區塊的正常終止) 和目的地 (處理例外狀況的 `__try` 區塊) 之間的所有作用中 `__except` 陳述式都必須執行。 這稱為區域回溯。  
  
 如果**再試一次**基於任何原因，包括跳出區塊提前終止區塊，系統會執行相關聯**最後**回溯堆疊程序的一部分的區塊。 在這種情況下， [AbnormalTermination](http://msdn.microsoft.com/library/windows/desktop/ms679265)函數會傳回 TRUE，如果已從內部呼叫**最後**區塊，否則會傳回 FALSE。  
  
 如果處理序在執行 `try-finally` 陳述式的中途遭到刪除，則不會呼叫終止處理常式。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [撰寫終止處理常式](../cpp/writing-a-termination-handler.md)   
 [結構化的例外處理 （C/c + +）](../cpp/structured-exception-handling-c-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [終止處理常式語法](http://msdn.microsoft.com/library/windows/desktop/ms681393)
