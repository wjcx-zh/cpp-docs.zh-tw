---
title: "try-except 陳述式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_abnormal_termination_cpp"
  - "_exception_code_cpp"
  - "EXCEPTION_CONTINUE_SEARCH"
  - "_exception_info"
  - "__except"
  - "EXCEPTION_CONTINUE_EXECUTION"
  - "_exception_code"
  - "__except_cpp"
  - "_exception_info_cpp"
  - "EXCEPTION_EXECUTE_HANDLER"
  - "_abnormal_termination"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__try 關鍵字 [C++]"
  - "_abnormal_termination 關鍵字 [C++]"
  - "_exception_code 關鍵字 [C++]"
  - "_exception_info 關鍵字 [C++]"
  - "EXCEPTION_CONTINUE_EXECUTION 巨集"
  - "EXCEPTION_CONTINUE_SEARCH 巨集"
  - "EXCEPTION_EXECUTE_HANDLER 巨集"
  - "GetExceptionCode 函式"
  - "try-catch 關鍵字 [C++], try-except 關鍵字 [C++]"
  - "try-except 關鍵字 [C++]"
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# try-except 陳述式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 下列語法描述 try\-except 陳述式：  
  
## 語法  
  
```  
  
      __try   
{  
   // guarded code  
}  
__except ( expression )  
{  
   // exception handler code  
}  
```  
  
## 備註  
 **try\-except** 陳述式是 Microsoft C 和 C\+\+ 語言擴充功能，可讓目標應用程式在發生通常會終止程式執行的事件時取得控制。  這類事件稱為例外狀況，而處理例外狀況的機制稱為結構化例外狀況處理。  
  
 如需相關資訊，請參閱 [try\-finally 陳述式](../cpp/try-finally-statement.md)。  
  
 例外狀況可能以硬體或軟體為主。  即使應用程式無法從硬體或軟體例外狀況完全復原，結構化例外狀況處理仍可顯示錯誤資訊，並且對應用程式的內部狀態設陷，以協助診斷問題。  這在處理無法輕易重現的間歇性問題時特別有用。  
  
> [!NOTE]
>  結構化例外狀況處理可搭配 Win32 處理 C 和 C\+\+ 原始程式檔。  不過，它不是專為 C\+\+ 所設計。  使用 C\+\+ 例外狀況處理可確保您的程式碼更具可移植性。  此外，C\+\+ 例外狀況處理更有彈性，因為它可以處理任何類型的例外狀況。  針對 C\+\+ 程式，建議您使用 C\+\+ 例外狀況處理機制 \([try、catch 和 throw 陳述式](../cpp/try-throw-and-catch-statements-cpp.md)\)。  
  
 `__try` 子句後面的複合陳述式是主體或保護的區段。  `__except` 子句後面的複合陳述式則是例外狀況處理常式。  如果在執行保護區段的主體時引發例外狀況，則處理常式會指定要採取的一組動作。  執行程序如下所示：  
  
1.  執行保護的區段。  
  
2.  如果執行保護的區段時未發生例外狀況，則會在 `__except` 子句之後的陳述式繼續執行。  
  
3.  如果執行保護的區段時或是在保護的區段所呼叫的任何常式中發生例外狀況，則會求出 `__except` *expression* \(稱為 *filter* 運算式\) 的值，而得到的值會決定例外狀況的處理方式。  共有三個值：  
  
     **EXCEPTION\_CONTINUE\_EXECUTION \(–1\)**：例外狀況已解除。  在例外狀況發生的位置繼續執行。  
  
     **EXCEPTION\_CONTINUE\_SEARCH \(0\)**：例外狀況無法辨識。  繼續搜尋堆疊中的處理常式，首先搜尋包含 **try\-except** 陳述式，然後是具有次高優先順序的處理常式。  
  
     **EXCEPTION\_EXECUTE\_HANDLER \(1\)**：例外狀況已辨識。  執行 `__except` 複合陳述式將控制項傳送至例外狀況處理常式，然後在 `__except` 區塊之後繼續執行。  
  
 由於 **\_\_except** 運算式會以 C 運算式求值，因此限於單一值、條件運算式運算子或逗號運算子。  如果需要更廣泛的處理，運算式可以呼叫常式，傳回上面所列三個值的其中一個。  
  
 每個應用程式都有自己的例外狀況處理常式。  
  
 雖然不可跳入 `__try` 陳述式，但是可以從這類陳述式跳出。  如果處理序在執行 **try\-except** 陳述式的過程中終止，則不會呼叫例外狀況處理常式。  
  
 如需詳細資訊，請參閱知識庫文件 Q315937：＜如何：對 Visual C\+\+ 應用程式中的堆疊溢位設陷＞\(機器譯文\)。  
  
## \_\_leave 關鍵字  
 `__leave` 關鍵字只有在 `try-except` 陳述式的保護區段內才有效，而其作用是跳至保護區段的結尾。  然後在例外狀況處理常式之後的第一個陳述式繼續執行。  
  
 `goto` 陳述式也可以跳出保護的區段，而且不會像在 `try-finally` 陳述式中一樣降低效能，因為堆疊回溯不會發生。  不過，建議您使用 `__leave` 關鍵字而不要使用 `goto` 陳述式，因為這樣在處理大型或複雜的保護區域時，比較不會發生程式設計錯誤。  
  
### 結構化例外狀況處理內建函式  
 結構化例外狀況處理提供兩種內建函式，可搭配 **try\-except** 陳述式使用：**GetExceptionCode** 和 **GetExceptionInformation**。  
  
 **GetExceptionCode** 會傳回例外狀況代碼 \(32 位元整數\)。  
  
 內建函式 **GetExceptionInformation** 會傳回結構的指標，其中包含有關例外狀況的其他資訊。  透過這個指標就可以存取發生硬體例外狀況當時的電腦狀態。  結構如下所示：  
  
```  
struct _EXCEPTION_POINTERS {  
      EXCEPTION_RECORD *ExceptionRecord,  
      CONTEXT *ContextRecord }  
```  
  
 指標類型 \_**EXCEPTION\_RECORD** 和 \_**CONTEXT** 是在 Include 檔案 EXCPT.H 中定義。  
  
 您可以在例外狀況處理常式內使用 **GetExceptionCode**。  不過，**GetExceptionInformation** 只能在例外狀況篩選條件運算式內使用。  它所指向的資訊通常位於堆疊上，而且在控制項傳送至例外狀況處理常式之後就不再提供。  
  
 內建函式 **AbnormalTermination** 是在終止處理常式內提供。  如果 `try-finally` 陳述式的主體循序終止，上述函式就會傳回 0。  在所有其他情況下，它會傳回 1。  
  
 EXCPT.H 會為這些內建定義一些替代名稱：  
  
 **GetExceptionCode** 相當於 \_exception\_code  
  
 **GetExceptionInformation** 相當於 \_exception\_info  
  
 **AbnormalTermination** 相當於 \_abnormal\_termination  
  
## 範例  
 `// exceptions_try_except_Statement.cpp`  
  
 `// Example of try-except and try-finally statements`  
  
 `#include <stdio.h>`  
  
 `#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION`  
  
 `#include <excpt.h>`  
  
 `int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep) {`  
  
 `puts("in filter.");`  
  
 `if (code == EXCEPTION_ACCESS_VIOLATION) {`  
  
 `puts("caught AV as expected.");`  
  
 `return EXCEPTION_EXECUTE_HANDLER;`  
  
 `}`  
  
 `else {`  
  
 `puts("didn't catch AV, unexpected.");`  
  
 `return EXCEPTION_CONTINUE_SEARCH;`  
  
 `};`  
  
 `}`  
  
 `int main()`  
  
 `{`  
  
 `int* p = 0x00000000;   // pointer to NULL`  
  
 `puts("hello");`  
  
 `__try{`  
  
 `puts("in try");`  
  
 `__try{`  
  
 `puts("in try");`  
  
 `*p = 13;    // causes an access violation exception;`  
  
 `}__finally{`  
  
 `puts("in finally. termination: ");`  
  
 `puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");`  
  
 `}`  
  
 `}__except(filter(GetExceptionCode(), GetExceptionInformation())){`  
  
 `puts("in except");`  
  
 `}`  
  
 `puts("world");`  
  
 `}`  
  
## 輸出  
  
```  
hello  
in try  
in try  
in filter.  
caught AV as expected.  
in finally. termination:  
        abnormal  
in except  
world  
```  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)   
 [結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)