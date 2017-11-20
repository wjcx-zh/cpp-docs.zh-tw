---
title: "try-except 陳述式 (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ea7526648d5879a224c3bc1ffd6c76dfc986c0c7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="try-except-statement-c"></a>try-except 陳述式 (C)
**Microsoft 特定的**  
  
 **try-except** 陳述式是 Microsoft C 語言的延伸模組，可讓應用程式在發生通常會終止程式執行的事件時取得程式控制權。 這類事件稱為例外狀況，而處理例外狀況的機制稱為結構化例外狀況處理。  
  
 例外狀況可能以硬體或軟體為主。 即使應用程式無法從硬體或軟體例外狀況完全復原，結構化例外狀況處理仍可顯示錯誤資訊，並且對應用程式的內部狀態設陷，以協助診斷問題。 這在處理無法輕易重現的間歇性問題時特別有用。  
  
## <a name="syntax"></a>語法  
 *try-except-statement*：  
 **__try**  *compound-statement*  
  
 **__except (**  *expression*  **)**  *compound-statement*  
  
 `__try` 子句後面的複合陳述式是保護的區段。 `__except` 子句後面的複合陳述式則是例外狀況處理常式。 如果在執行保護區段時引發例外狀況，則處理常式會指定要採取的一組動作。 執行程序如下所示：  
  
1.  執行保護的區段。  
  
2.  如果執行保護的區段時未發生例外狀況，則會在 `__except` 子句之後的陳述式繼續執行。  
  
3.  如果在執行保護的區段時或在保護區段所呼叫的任何常式中發生例外狀況，就會評估 `__except` 運算式，並由傳回值決定例外狀況處理方式。 共有三個值：  
  
     `EXCEPTION_CONTINUE_SEARCH`：無法辨識例外狀況。 繼續搜尋堆疊中的處理常式，首先搜尋包含 **try-except** 陳述式，然後是具有次高優先順序的處理常式。  
  
     `EXCEPTION_CONTINUE_EXECUTION`：可辨識例外狀況，但已解除。 在例外狀況發生的位置繼續執行。  
  
     `EXCEPTION_EXECUTE_HANDLER`：可辨識例外狀況。 執行 `__except` 複合陳述式，然後在發生例外狀況的點繼續執行，將控制項傳送給例外狀況處理常式。  
  
 由於 `__except` 運算式會以 C 運算式求值，因此限於單一值、條件運算式運算子或逗號運算子。 如果需要更廣泛的處理，運算式可以呼叫常式，傳回上面所列三個值的其中一個。  
  
> [!NOTE]
>  結構化例外狀況處理可搭配 C 和 C++ 原始程式檔使用。 不過，它不是專為 C++ 所設計。 使用 C++ 例外狀況處理可確保您的程式碼更具可移植性。 此外，C++ 例外狀況處理機制更有彈性，因為它可以處理任何類型的例外狀況。  
  
> [!NOTE]
>  針對 C++ 程式，應該使用 C++ 例外狀況處理，而不是結構化例外狀況處理。 如需詳細資訊，請參閱《C++ 語言參考》中的[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)。  
  
 應用程式中的每個常式都可以有其本身的例外狀況處理常式。 `__except` 運算式會在 `__try` 主體的範圍內執行。 這表示它可以存取在此宣告的任何區域變數。  
  
 `__leave` 關鍵字在 **try-except** 陳述式區塊內有效。 `__leave` 的作用是跳至 **try-except** 區塊的結尾。 會在例外狀況處理常式結束之後繼續執行。 雖然 `goto` 陳述式可用來達到相同的結果，但 `goto` 陳述式會造成堆疊回溯的情形。 因為不包含堆疊回溯，因此使用 `__leave` 陳述式會更有效率。  
  
 使用 `longjmp` 執行階段函式結束 **try-except** 陳述式屬於異常終止。 雖然不可跳入 `__try` 陳述式，但是可以從這類陳述式跳出。 如果處理序在執行 **try-except** 陳述式的過程中終止，則不會呼叫例外狀況處理常式。  
  
## <a name="example"></a>範例  
 以下是例外狀況處理常式和終止處理常式的範例。 如需終止處理常式的詳細資訊，請參閱 [try-finally 陳述式](../c-language/try-finally-statement-c.md)。  
  
```  
.  
.  
.  
puts("hello");  
__try{  
   puts("in try");  
   __try{  
      puts("in try");  
      RAISE_AN_EXCEPTION();  
   }__finally{  
      puts("in finally");  
   }  
}__except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ){  
   puts("in except");  
}  
puts("world");  
```  
  
 這是範例的輸出，註解加在右邊：  
  
```  
hello  
in try              /* fall into try                     */  
in try              /* fall into nested try                */  
in filter           /* execute filter; returns 1 so accept  */  
in finally          /* unwind nested finally                */  
in except           /* transfer control to selected handler */  
world               /* flow out of handler                  */  
```  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [try-except 陳述式](../cpp/try-except-statement.md)