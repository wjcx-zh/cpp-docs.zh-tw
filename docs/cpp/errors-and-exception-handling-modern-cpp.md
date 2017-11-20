---
title: "錯誤和例外狀況處理 （現代 c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ab5b54c820095b54be28a5868505d07f9b0e39d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="errors-and-exception-handling-modern-c"></a>錯誤和例外狀況處理 (現代 C++)
在現代 c + +，在大部分情況下，報告和處理邏輯錯誤和執行階段錯誤的慣用的方法是使用例外狀況。 堆疊可能包含有要知道如何處理它的內容的函式偵測到錯誤的函式之間的數個函式呼叫時，這是特別有用。 例外狀況所偵測的錯誤，以傳遞到呼叫堆疊資訊的程式碼提供正式的妥善定義的方式。  
  
 程式錯誤通常分為兩類： 邏輯錯誤所造成程式設計錯誤，例如，「 索引超出範圍 」 錯誤和執行階段錯誤，例如已超出控制項的程式設計人員，「 網路服務無法使用 」發生錯誤。 藉由傳回值，表示錯誤代碼或狀態碼對於特定的函式，或藉由設定的全域變數，呼叫端可能會選擇性地擷取以查看每個函式呼叫後於在 c-style 程式設計和 COM，管理錯誤報告是否發生錯誤。 比方說，COM 程式設計通訊錯誤，以呼叫端，使用的 HRESULT 傳回值，並 Win32 API 具有 GetLastError 函式來擷取最後一個呼叫堆疊報告的錯誤。 在這兩種情況下，是由識別程式碼，然後適當地回應其呼叫端。 如果呼叫端未明確地處理錯誤程式碼，程式可能會損毀，而不發出警告，或繼續使用不正確的資料來執行，產生不正確的結果。  
  
 例外狀況，最好是使用在現代 c + + 中，原因如下：  
  
-   例外狀況會強制辨識錯誤狀況，並處理呼叫的程式碼。 未處理例外狀況停止程式執行。  
  
-   例外狀況會跳到可處理錯誤的呼叫堆疊中的點。 中繼函式可以讓傳播例外狀況。 它們沒有協調與其他圖層。  
  
-   例外狀況堆疊回溯機制終結根據妥善定義的規則的範圍內的所有物件之後擲回例外狀況。  
  
-   例外狀況可讓您清楚分隔偵測到錯誤的程式碼和處理錯誤程式碼。  
  
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
  
 C + + 中的例外狀況類似 C# 和 Java 等語言。 中`try`如果例外狀況封鎖*擲回*會很*攔截*第一部相關聯`catch`區塊型別與相符的例外狀況。 也就是說，執行會跳從`throw`陳述式來`catch`陳述式。 如果找不到任何可用的 catch 區塊，`std::terminate`叫用並結束程式。 在 c + +，則可能擲回任何類型;不過，我們建議您擲回的類型是直接或間接衍生自`std::exception`。 在上述範例中，例外狀況型別[invalid_argument](../standard-library/invalid-argument-class.md)，標準程式庫中定義[ \<x >](../standard-library/stdexcept.md)標頭檔。 C + + 不提供，而且不需要，`finally`區塊，以確定發生例外狀況，就會釋放所有資源。 擷取資源是初始化 (RAII) 慣用語，使用智慧型指標，提供資源清除所需的功能。 如需詳細資訊，請參閱[如何： 例外狀況安全的設計](../cpp/how-to-design-for-exception-safety.md)。 如需 c + + 堆疊回溯機制的資訊，請參閱[例外狀況和堆疊回溯](../cpp/exceptions-and-stack-unwinding-in-cpp.md)。  
  
## <a name="basic-guidelines"></a>基本指導方針  
 強固的錯誤處理是在任何程式設計語言中一項挑戰。 雖然例外狀況會提供數個支援良好的錯誤處理功能，但是它們不能為您執行所有工作。 若要了解例外狀況機制的優點，記住例外狀況在設計您的程式碼。  
  
-   使用判斷提示檢查應該永遠不會發生的錯誤。 若要檢查的錯誤，可能會發生，例如，輸入驗證參數的公用函式中的錯誤，使用例外狀況。 如需詳細資訊，請參閱下一節**例外狀況與。判斷提示**。  
  
-   處理錯誤的程式碼可能會偵測到錯誤的程式碼分隔一或多個中介的函式呼叫時，請使用例外狀況。 請考慮是否要改用錯誤碼在迴圈中效能嚴重不足時處理錯誤程式碼會偵測到它的程式碼緊密結合。 
  
-   每個函式，可能會擲回或傳播例外狀況，提供三個例外狀況保證： 強力保證、 基本保證或 nothrow (noexcept) 保證。 如需詳細資訊，請參閱[如何： 例外狀況安全的設計](../cpp/how-to-design-for-exception-safety.md)。  
  
-   依值擲回例外狀況，攔截它們的參考。 不會攔截無法處理。 
  
-   不要使用例外狀況規格，C + + 11 中已被取代。 如需詳細資訊，請參閱下一節**例外狀況規格與 noexcept**。  
  
-   當這些條款適用於使用標準程式庫例外狀況類型。 衍生的自訂例外狀況類型從[例外狀況類別](../standard-library/exception-class.md)階層。  
  
-   不允許逸出從解構函式或記憶體解除配置函式的例外狀況。  
  
## <a name="exceptions-and-performance"></a>例外狀況和效能  
 例外狀況機制具有很少的效能成本如果擲不回任何例外狀況。 如果擲回例外狀況，堆疊周遊的成本，回溯是大致上相當於函式呼叫的成本。 其他資料結構所需來追蹤呼叫堆疊之後`try`進入區塊時，並發生例外狀況時回溯堆疊所需的其他指示。 不過，在大部分情況下，在效能及記憶體使用量成本並不重要。 例外狀況對效能產生負面的影響是有可能是重要只有非常記憶體限制的系統上，或在效能關鍵執行迴圈錯誤很可能會定期執行，而處理它的程式碼會將它報告的程式碼緊密結合。 在任何情況下，就無法知道實際成本的例外狀況，而不需要程式碼剖析和測量。 即使是在少數的情況時的成本會很可觀，您可以衡量其針對增加的正確性、 更容易維護性，以及設計良好的例外狀況原則所提供的其他優點。  
  
## <a name="exceptions-vs-assertions"></a>與判斷提示例外狀況  
 例外狀況和判斷提示是兩個不同的機制，可在程式中偵測到執行階段錯誤。 使用判斷提示也不應為 true，如果您的程式碼是正確的開發期間，測試條件。 沒有使用例外狀況，因為此錯誤表示在程式碼中的項目已固定，處理這類錯誤點並不表示該程式必須在執行階段從復原的條件。 判斷提示會停止執行的陳述式，使您可以檢查程式狀態，在偵錯工具。例外狀況會繼續執行，從第一個適當的 catch 處理常式。 使用例外狀況來檢查錯誤狀況可能發生在執行階段中，即使您的程式碼是正確的比方說，「 找不到檔案 」 或 「 記憶體不足。 」 您可能想要復原因這些情況中，即使復原只要輸出至記錄訊息並結束程式。 使用例外狀況，一律檢查公用函式的引數。 即使您的函式是無錯誤，您可能沒有使用者可能會傳遞給它的引數的完整控制權。  
  
## <a name="c-exceptions-versus-windows-seh-exceptions"></a>與 Windows SEH 例外狀況的 c + + 例外狀況  
 C 和 c + + 程式可以使用結構化例外狀況處理 (SEH) 機制，在 Windows 作業系統中。 SEH 的概念類似 c + + 例外狀況，不同之處在於會使用 SEH `__try`， `__except`，和`__finally`而不是建構`try`和`catch`。 在 Visual c + +、 c + + 例外狀況被實作 SEH。 不過，當您撰寫 c + + 程式碼，使用 c + + 例外狀況語法。  
  
 如需 SEH 的詳細資訊，請參閱[結構化例外狀況處理 （C/c + +）](../cpp/structured-exception-handling-c-cpp.md)。  
  
## <a name="exception-specifications-and-noexcept"></a>例外狀況規格與 noexcept  
 例外狀況規格是 c + + 中導入，做為指定的函式可能會擲回的例外狀況的方式。 不過，例外狀況規格證明有問題，在實務上，而且已被取代的 C + + 11 草稿標準。 我們建議您不要使用例外狀況規格，除了`throw()`，表示函式可讓任何逸出的例外狀況。 如果您必須使用類型的例外狀況規格`throw(`*類型*`)`，注意 Visual c + + 偏離標準所規定的方式。 如需詳細資訊，請參閱[例外狀況規格 (throw)](../cpp/exception-specifications-throw-cpp.md)。 `noexcept`規範做為慣用的替代方式在 C + + 11 引進`throw()`。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 例外狀況和非例外狀況代碼之間的介面](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)   
 [歡迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)
