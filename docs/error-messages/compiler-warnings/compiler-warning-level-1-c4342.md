---
title: "編譯器警告 (層級 1) C4342 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4342"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4342"
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 編譯器警告 (層級 1) C4342
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

行為變更: 呼叫了 'function'，但是先前版本中呼叫的是成員運算子  
  
 在舊版 Visual C\+\+ 中，呼叫了成員，但這種行為已經變更，而編譯器會在命名空間範圍中找到最符合項目。  
  
 如果找到了成員運算子，編譯器會 \(舊版不會\) 考慮任何命名空間範圍運算子。  如果在命名空間範圍有更符合的項目，目前的編譯器會正確地呼叫它，而舊版編譯器則不會考慮。  
  
 這項警告應該在您順利移植程式碼至目前版本之後停用。編譯器可能會誤報，在程式碼並沒有行為變更處產生這項警告。  
  
 此警告在預設情況下為關閉的。  如需詳細資訊，請參閱[預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下列範例會產生 C4342：  
  
```  
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