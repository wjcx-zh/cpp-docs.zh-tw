---
title: 字串和我-O 格式化 （現代 c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 391648d71fa3d38a0f704a014c163b7f8b102e40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422380"
---
# <a name="string-and-io-formatting-modern-c"></a>字串和 I/O 格式化 (現代 C++)
C + + [iostreams](../standard-library/iostream.md)能夠格式化字串 I/O。 例如，下列程式碼示範如何設定 cout 來格式化整數，以十六進位方式，先關閉目前的狀態儲存及重新設定，之後，因為一旦狀態格式傳遞給 cout，它維持該狀態的變更，不只是針對一個線條之前輸出程式碼。  
  
```cpp  
#include <iostream>  
#include <iomanip>  
  
using namespace std;  
  
int main()   
{  
    ios state(nullptr);  
  
    cout << "The answer in decimal is: " << 42 << endl;  
  
    state.copyfmt(cout); // save current formatting  
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers  
        << hex   
        << uppercase   
        << setw(8)   
        << setfill('0')   
        << 42            // the actual value we wanted to print out  
        << endl;  
    cout.copyfmt(state); // restore previous formatting  
}  
  
```  
  
 這可以完全是很麻煩，因為在許多情況下。 或者，您可以提升 c + + 程式庫中，從使用 Boost.Format，即使它並非標準用法。 您可以下載從任何提升文件庫[Boost](http://www.boost.org/)網站。  
  
 Boost.Format 的一些優點包括：  
  
-   安全： 類型安全，並擲回例外狀況的錯誤 — 例如，太少或太多個項目的規格。  
  
-   可延伸： 適用於進行串流處理任何類型。  
  
-   簡便： 標準 Posix 和類似的格式字串。  
  
 雖然 c + + 建置 Boost.Format [iostreams](../standard-library/iostream-programming.md)，這是安全且可延伸，它們不是效能最佳化。 當您需要效能最佳化時，請考慮 C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)和[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)，這是快速且容易使用。 不過，不是可延伸或安全，以免產生漏洞。 （存在的安全版本，但是它們會造成效能稍微降低。 如需詳細資訊，請參閱[printf_s、 _printf_s_l、 wprintf_s、 _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)和[sprintf_s、 _sprintf_s_l、 swprintf_s、 _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md))。  
  
 下列程式碼示範一些格式功能的提升。  
  
```cpp  
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );  
    // s contains "hello hello world"    
  
    for( auto i = 0; i < names.size(); ++i )  
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];  
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789  
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [歡迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 語言參考](../cpp/cpp-language-reference.md)   
 [C++ 標準程式庫](../standard-library/cpp-standard-library-reference.md)   
 [\<iostream >](../standard-library/iostream.md)   
 [\<限制 >](../standard-library/limits.md)   
 [\<iomanip>](../standard-library/iomanip.md)
