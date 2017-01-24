---
title: "try、throw 和 catch 陳述式 (C++) | Microsoft Docs"
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
  - "catch_cpp"
  - "throw"
  - "try_cpp"
  - "try"
  - "throw_cpp"
  - "catch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "catch 關鍵字 [C++]"
  - "關鍵字 [c + +] 例外狀況處理"
  - "C + + 例外狀況處理陳述式語法"
  - "try-catch 關鍵字 [c + +]，關於 try-catch 例外狀況處理"
  - "throw 關鍵字 [C++]"
  - "try-catch 關鍵字 [C++]"
  - "try-catch 關鍵字 [c + +] 例外狀況處理"
  - "throw 陳述式擲回的例外狀況"
  - "try-catch 關鍵字 [c + +]、 throw 關鍵字 [c + +] s"
  - "擲回例外狀況，實作 c + + 例外狀況處理"
  - "擲回例外狀況"
  - "throw 關鍵字 [c + +] throw （） 和 throw （...）"
ms.assetid: 15e6a87b-b8a5-4032-a7ef-946c644ba12a
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# try、throw 和 catch 陳述式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要在 C++ 中實作例外狀況處理，您可以使用 `try`、`throw` 和 `catch` 運算式。  
  
 首先，使用 `try` 區塊包含一個或多個可能會擲回例外狀況的陳述式。  
  
 `throw` 運算式會發出 `try` 區塊發生例外狀況的訊號 (通常是錯誤)。 您可以將任何類型的物件當成 `throw` 運算式的運算元使用。 這個物件通常用來傳達與錯誤有關的資訊。 在大部分情況下，我們建議您使用 [std:: exception](../standard-library/exception-class1.md) 類別或其中一個標準程式庫中定義的衍生類別。 如果有任何不適用的類別，建議您從 `std::exception` 自行衍生例外狀況類別。  
  
 若要處理可能擲回的例外狀況，請在 `catch` 區塊之後緊接著實作一個或多個 `try` 區塊。 每個 `catch` 區塊皆會指定可處理的例外狀況類型。  
  
 此範例示範 `try` 區塊及其處理常式。 假設 `GetNetworkResource()` 透過網路連線取得資料，且兩個例外狀況類型是衍生自 `std::exception` 的使用者定義類別。 請注意，`const` 陳述式的 `catch` 參考會攔截例外狀況。 建議您依照值擲回例外狀況並依 const 參考攔截這些例外狀況。  
  
## <a name="example"></a>範例  
  
```  
  
MyData md;  
try {  
   // Code that could throw an exception  
   md = GetNetworkResource();  
}  
catch (const networkIOException& e) {  
   // Code that executes when an exception of type  
   // networkIOException is thrown in the try block  
   // ...  
   // Log error message in the exception object  
   cerr << e.what();  
}  
catch (const myDataFormatException& e) {  
   // Code that handles another exception type  
   // ...  
   cerr << e.what();  
}  
  
// The following syntax shows a throw expression  
MyData GetNetworkResource()  
{  
   // ...  
   if (IOSuccess == false)  
      throw networkIOException("Unable to connect");  
   // ...  
   if (readError)  
      throw myDataFormatException("Format error");   
   // ...  
}  
```  
  
## <a name="remarks"></a>備註  
 `try` 子句之後的程式碼是程式碼的保護區段。  `throw` 運算式 *會擲回*— 也就是引發 — 例外狀況。 `catch` 子句之後的程式碼區塊是例外狀況處理常式。 這個處理常式， *攔截* ，則會擲回的例外狀況中的型別 `throw` 和 `catch` 運算式都相容。 如需管理中的型別符合規則的清單 `catch` 區塊，請參閱 [評估如何 Catch 區塊的](../cpp/how-catch-blocks-are-evaluated-cpp.md)。 如果 `catch` 陳述式指定省略符號 (...) 而不是類型，則 `catch` 區塊會處理例外狀況的每一種類型。 當您編譯與 [/EHa](../build/reference/eh-exception-handling-model.md) 選項，這些可能包括 C 結構化例外狀況，以及系統產生或應用程式所產生的非同步例外，例如記憶體保護、 除數為零，以及浮點數違規。 由於會按照程式順序處理 `catch` 區塊，以尋找相符的類型，因此省略符號處理常式必須是相關聯的 `try` 區塊中的最後一個處理常式。 使用 `catch(...)` 時請小心；除非 catch 區塊知道如何處理所攔截到的特定例外狀況，否則不可允許程式繼續執行。 通常，`catch(...)` 區塊的用途是在程式停止執行之前記錄錯誤和執行特殊清除。  
  
 不含運算元的 `throw` 運算式會重新擲回目前正在處理的例外狀況。 重新擲回例外狀況時，建議使用此表單，因為其中保留了原始例外狀況的多型類型資訊。 這類運算式只能在 `catch` 處理常式中或從 `catch` 處理常式內部呼叫的函式中使用。 重新擲回的例外狀況物件是原始的例外狀況物件，而不是複本。  
  
```  
try {  
   throw CSomeOtherException();  
}  
catch(...) {  
   // Catch all exceptions – dangerous!!!  
   // Respond (perhaps only partially) to the exception, then  
   // re-throw to pass the exception to some other handler  
   // ...  
   throw;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [C + + 例外狀況處理](../cpp/cpp-exception-handling.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [未處理的 c + + 例外狀況](../cpp/unhandled-cpp-exceptions.md)   
 [__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)