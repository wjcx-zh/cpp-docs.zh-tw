---
title: "編譯器警告 （層級 1） C4342 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4342
dev_langs:
- C++
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
caps.latest.revision: 10
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: c4a2afbc3ced186b0db63b22b3cc5c2b27204c71
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4342"></a>編譯器警告 (層級 1) C4342
行為變更: '*函式*' 呼叫，但在舊版中被呼叫的是成員運算子  
  
 在 Visual Studio 2002 之前的 Visual c + + 版本中，呼叫成員時，但是這種行為已變更，而且編譯器現在會尋找最符合命名空間範圍中。  
  
 如果找不到成員運算子，編譯器會先前不考慮任何命名空間範圍運算子。 如果沒有更好的相符項目在命名空間範圍內，目前的編譯器正確呼叫它，而舊版編譯器不會考慮。  
  
 在您成功地移植程式碼，以最新版本之後，應該停用這個警告。  編譯器可能會誤報，產生這個警告的程式碼在沒有任何行為變更。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱[編譯器警告為關閉的預設](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列範例會產生 C4342:  
  
```cpp  
// C4342.cpp  
// compile with: /EHsc /W1  
#include <fstream>  
#pragma warning(default: 4342)  
using namespace std;  
struct X : public ofstream {  
   X();  
};  
  
X::X() {  
   open( "ofs_bug_ev.txt." );  
   if ( is_open() ) {  
      *this << "Text" << "<-should be text" << endl;   // C4342  
      *this << ' ' << "<-should be space symbol" << endl;   // C4342  
   }  
}  
  
int main() {  
   X b;  
   b << "Text" << "<-should be text" << endl;  
   b << ' ' << "<-should be space symbol" << endl;  
}  
```
