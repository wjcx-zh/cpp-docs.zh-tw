---
title: "錯誤和例外狀況處理 (現代 C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 錯誤和例外狀況處理 (現代 C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在現代 c + +，在大部分情況下，報告和處理邏輯錯誤和執行階段錯誤，最好是使用例外狀況。 特別是當堆疊可能包含多個函式呼叫之間偵測到錯誤的函式和函式具有要知道如何處理它的內容。 例外狀況會提供正式且定義完善的方式偵測到錯誤，以傳遞到呼叫堆疊資訊的程式碼。  
  
 程式錯誤通常分為兩類︰ 邏輯錯誤所造成的程式設計錯誤，例如，「 索引超出範圍 」 錯誤，而執行階段錯誤所控制的程式設計師，比方說，「 網路服務無法使用 」 的錯誤。 傳回值，表示錯誤程式碼或特定的函式中，狀態碼，或設定呼叫者可以選擇性地擷取每個函式呼叫，以查看是否發生錯誤之後的全域變數，在 c-style 程式設計和 COM 中，錯誤報告被管理。 例如，COM 程式設計通訊錯誤給呼叫端，使用 HRESULT 傳回值，並 Win32 API 具有 GetLastError 函式來擷取最後的呼叫堆疊報告錯誤。 在這兩種情況下，是由呼叫者識別程式碼，並適當地回應給它。 如果呼叫端未明確處理的錯誤程式碼，程式可能會當機，而不發出警告，或繼續執行含有不正確的資料，並產生不正確的結果。  
  
 例外狀況，最好是使用在現代 c + + 中，原因如下︰  
  
-   例外狀況會強制辨識錯誤狀況，並處理呼叫的程式碼。 未處理例外狀況停止程式執行。  
  
-   例外狀況會跳到可以處理錯誤的呼叫堆疊中的點。 中繼函式可以讓傳播的例外狀況。 它們不需要協調與其他層。  
  
-   例外狀況堆疊回溯機制終結根據妥善定義的規則的範圍內的所有物件之後擲回例外狀況。  
  
-   例外狀況可讓您清楚地分隔偵測到錯誤的程式碼，以及處理錯誤的程式碼。  
  
 下列簡化的範例顯示擲回和攔截 c + + 中的例外狀況的必要語法。  
  
```cpp  
  
#include <stdexcept>  
#include <limits>  
#include <iostream>  
  
using namespace std;  
class MyClass  
{  
public:  
   void MyFunc(char c)  
   {  
      if(c < numeric_limits<char>::max())  
         throw invalid_argument("MyFunc argument too large.");  
      //...  
   }  
};  
  
int main()  
{  
   try  
   {  
      MyFunc(256); //cause an exception to throw  
   }  
  
   catch(invalid_argument& e)  
   {  
      cerr << e.what() << endl;  
      return -1;  
   }  
   //...  
   return 0;  
}  
  
```  
  
 在 c + + 例外狀況類似 C# 和 Java 等語言。 在 `try` 封鎖，如果例外狀況 *擲回* 將予以 *攔截* 第一部相關聯 `catch` 區塊型別與相符的例外狀況。 也就是說，執行會跳從 `throw` 陳述式來 `catch` 陳述式。 如果找不到沒有可用的 catch 區塊， `std::terminate` 叫用並結束程式。 在 c + +，任何型別可能會擲回。不過，我們建議您擲回的型別是直接或間接衍生自 `std::exception`。 在上述範例中，例外狀況型別 [invalid_argument](../standard-library/invalid-argument-class.md), ，標準程式庫中定義 [\< stdexcept>](../standard-library/stdexcept.md) 標頭檔。 C + + 不提供，且不需要 `finally` 區塊，藉此確定如果擲回例外狀況時釋放所有資源。 擷取資源是初始化 (RAII) 慣用語使用智慧型指標，其中會提供資源清除所需的功能。 如需詳細資訊，請參閱 [How to︰ 例外狀況安全的設計](../cpp/how-to-design-for-exception-safety.md)。 如需 c + + 堆疊回溯機制的資訊，請參閱 [例外狀況和堆疊回溯](../cpp/exceptions-and-stack-unwinding-in-cpp.md)。  
  
## <a name="basic-guidelines"></a>基本指導方針  
 強固的錯誤處理是在任何程式設計語言中具挑戰性。 例外狀況會提供數個支援良好的錯誤處理功能，雖然它們不能為您執行所有工作。 若要實現例外狀況機制的優點，記住例外狀況在設計您的程式碼。  
  
-   使用判斷提示來檢查應該永遠不會發生的錯誤。 使用例外狀況，以檢查可能發生的錯誤，例如，輸入驗證參數的公用函式中的錯誤。 如需詳細資訊，請參閱下一節 **vs 例外狀況。判斷提示**。  
  
-   處理錯誤的程式碼可能會偵測到錯誤的程式碼分隔一或多個中介的函式呼叫時，請使用例外狀況。 請考慮是否要改用錯誤碼在效能關鍵的迴圈時處理錯誤的程式碼會偵測到它的程式碼緊密結合。 如需何時不該使用例外狀況的詳細資訊，請參閱 [(NOTINBUILD) 時不使用例外狀況](http://msdn.microsoft.com/zh-tw/e810df8b-2217-4e81-bae5-02f0a69f1346)。  
  
-   對於每個函式，可能會擲回或傳播例外狀況，提供三個例外狀況保證︰ 強力保證、 基本的保證或 nothrow (noexcept) 保證。 如需詳細資訊，請參閱 [How to︰ 例外狀況安全的設計](../cpp/how-to-design-for-exception-safety.md)。  
  
-   依照值擲回例外狀況，攔截它們的參考。 不會攔截您無法處理。 如需詳細資訊，請參閱 [擲和攔截例外狀況 （c + +） (NOTINBUILD) 指導方針](http://msdn.microsoft.com/zh-tw/0a9b0a3a-64c5-43f5-a080-fca69b89e839)。  
  
-   請勿使用例外狀況規格，C + + 11 中已被取代。 如需詳細資訊，請參閱下一節 **例外狀況規格與 noexcept**。  
  
-   套用時，請使用標準程式庫例外狀況類型。 衍生自訂例外狀況類型從 [例外狀況類別](../standard-library/exception-class1.md) 階層。 如需詳細資訊，請參閱 [(NOTINBUILD) 如何︰ 使用標準程式庫例外狀況物件](http://msdn.microsoft.com/zh-tw/ad1fb785-ed4e-4d94-8e84-964353aed7b6)。  
  
-   不允許例外狀況從解構函式逸出或記憶體解除配置函式。  
  
## <a name="exceptions-and-performance"></a>例外狀況和效能  
 例外狀況機制有極小的效能成本，如果擲不回任何例外狀況。 如果發生例外狀況時，堆疊周遊的成本和回溯是大概相當於函式呼叫的成本。 其他資料結構所需追蹤呼叫堆疊之後 `try` 進入區塊時，並擲回例外狀況時回溯堆疊所需的其他指示。 不過，在大部分情況下，在效能和記憶體耗用量的成本並不重要。 在效能上的例外狀況不良的影響很可能是重大只有非常記憶體限制在系統上，或在效能嚴重不足會針對其中錯誤可能會定期執行，而處理它的程式碼會報告它的程式碼有著緊密的結合。 在任何情況下，就無法得知實際成本的例外狀況，而不需要程式碼剖析和測量。 即使是在少數的情況時的成本是很重要，您可以衡量它免於提高的正確性、 更容易維護性，以及其他設計完善的例外狀況原則所提供的優點。  
  
## <a name="exceptions-vs-assertions"></a>與判斷提示例外狀況  
 例外狀況和判斷提示兩個不同的機制來偵測程式中的執行階段錯誤。 使用判斷提示應該永遠不會是您的程式碼是否正確，則為 true 的開發期間，測試條件。 沒有使用例外狀況，此錯誤表示，它在程式碼中必須固定的因為處理這類錯誤點並不代表該程式必須在執行階段從復原的條件。 判斷提示會停止執行的陳述式，使您可以檢查程式狀態，在偵錯工具。例外狀況會繼續從第一個適當的 catch 處理常式的執行。 用來檢查即使您的程式碼是正確的比方說，「 找不到檔案 」 或 「 記憶體不足。 」，在執行階段可能發生的錯誤狀況的例外狀況 您可能想要復原因這些情況中，即使復原只是將訊息輸出至記錄檔，並結束程式。 一定要檢查公用函式的引數使用的例外狀況。 即使您的函式是無錯誤，您可能沒有使用者可能會傳遞給它的引數的完整控制權。  
  
## <a name="c-exceptions-versus-windows-seh-exceptions"></a>與 Windows SEH 例外狀況的 c + + 例外狀況  
 C 和 c + + 程式可以使用結構化的例外處理 (SEH) 機制，Windows 作業系統中。 在 SEH 概念類似 c + + 例外狀況，不過，使用 SEH `__try`, ，`__except`, ，和 `__finally` 而不是建構 `try` 和 `catch`。 Visual c + +、 c + + 例外狀況被實作 SEH。 不過，當您撰寫 c + + 程式碼，使用 c + + 例外狀況語法。  
  
 如需 SEH 的詳細資訊，請參閱 [結構化例外處理 （C/c + +）](../cpp/structured-exception-handling-c-cpp.md)。  
  
## <a name="exception-specifications-and-noexcept"></a>例外狀況規格與 noexcept  
 例外狀況規格是 c + + 中導入，用來指定函式可能擲回的例外狀況。 不過，例外狀況規格證明在實務上，有問題，而且已被取代的 C + + 11 草稿標準。 我們建議您不要使用例外狀況規格，除了 `throw()`, ，表示例外狀況，允許任何例外狀況逸出。 如果您必須使用之型別的例外狀況規格 `throw(`*類型*`)`, ，請注意， [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 偏離標準所規定的方式。 如需詳細資訊，請參閱 [例外狀況規格 （擲回）](../cpp/exception-specifications-throw-cpp.md)。  `noexcept` 規範 C + + 11 中導入做為慣用的替代方案 `throw()`。  
  
## <a name="see-also"></a>另請參閱  
 [如何︰ 例外狀況和非例外狀況代碼之間的介面](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)   
 [歡迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [C + + 標準程式庫](../standard-library/cpp-standard-library-reference.md)