---
title: "字串和 I/O 格式化 (現代 C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 字串和 I/O 格式化 (現代 C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ [iostreams](../standard-library/iostream.md) 可進行格式化的字串 I\/O。  例如，下列程式碼示範如何先取消儲存目前狀態然後再重設，設定 cout 將整數格式化為十六進位的輸出，因為一旦狀態格式傳遞至 cout，會保持這種方式直到變更為止，而不只是針對一個程式碼行。  
  
```fortran  
#include <iostream>  
#include <iomanip>  
  
using namespace std;  
  
int main()   
{  
    ios state(nullptr);  
  
    cout << "The answer in decimal is: " << 42 << endl;  
  
    state.copyfmt(cout); // save current formatting  
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers  
        << hex   
        << uppercase   
        << setw(8)   
        << setfill('0')   
        << 42            // the actual value we wanted to print out  
        << endl;  
    cout.copyfmt(state); // restore previous formatting  
}  
  
```  
  
 這在許多情況下都完全難以處理。  或者，您可以使用 Boost C\+\+ 程式庫中的 Boost.Format，即使它是非標準的。  您可以從 [Boost](http://www.boost.org/) 網站下載任何 Boost 程式庫。  
  
 Boost.Format 的一些優點是：  
  
-   安全：類型安全，並針對錯誤擲回例外狀況 \-\- 例如，有太少或太多項目的規格。  
  
-   可延伸的：適用於可以進行資料流處理的任何類型。  
  
-   方便：標準 Posix 和類似的格式字串。  
  
 雖然 Boost.Format 是建置在 C\+\+ [iostreams](../standard-library/iostream-programming.md) 基礎上，是安全且可擴充的，但並非效能最佳化。  當您需要效能最佳化時，請考慮使用 C 的 [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 和 [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)，這是既快速又容易使用的。  然而，它們無法擴充或有安全性弱點。\(安全版本存在，但是產生些微的效能損失。  如需詳細資訊，請參閱 [printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) 和 [sprintf\_s、\_sprintf\_s\_l、swprintf\_s、\_swprintf\_s\_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)\)。  
  
 下列程式碼示範部分提升格式化功能。  
  
```cpp  
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );  
    // s contains "hello hello world"    
  
    for( auto i = 0; i < names.size(); ++i )  
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];  
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789  
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321  
  
```  
  
## 請參閱  
 [歡迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 語言參考](../cpp/cpp-language-reference.md)   
 [C\+\+ Standard Library](../standard-library/cpp-standard-library-reference.md)   
 [\<iostream\>](../standard-library/iostream.md)   
 [\<limits\>](../standard-library/limits.md)   
 [\< \> iomanip](../standard-library/iomanip.md)