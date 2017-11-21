---
title: "例外狀況處理差異 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cfa736c83dd76ff8b8f677daad54104ff507df03
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="exception-handling-differences"></a>例外狀況處理差異
結構化例外狀況處理和 C++ 例外狀況處理之間的主要差異，在於 C++ 例外狀況處理模型是處理類型，而 C 結構化例外狀況處理模型則是處理某種類型的例外狀況 (明確地說即 `unsigned int`)。 也就是說，C 例外狀況是以不帶正負號的整數值來識別，而 C++ 例外狀況則是以資料類型來識別。 在 C 中引發例外狀況時，每個可能的處理常式都會執行一個篩選器，以檢查 C 例外狀況內容並判斷應接受該例外狀況、將其傳遞至其他處理常式，或是要予以忽略。 C++ 中擲回例外狀況時，它可能是任何類型。  
  
 第二個差異是 C 結構化例外狀況處理模型稱為「非同步」，因為例外狀況會在正常控制流之後發生。 C++ 例外狀況處理機制則完全「同步」，這表示只有在擲回例外狀況時才會發生。  
  
 如果在 c + + 程式中引發 C 例外狀況時，它可以處理其相關聯的篩選器的結構化例外狀況處理常式或 c + +**攔截**處理常式，無論是以動態准例外狀況內容。 例如，下列 c + + 程式引發 C 例外狀況的 c + + 內**再試一次**內容：  
  
## <a name="example"></a>範例  
  
```  
// exceptions_Exception_Handling_Differences.cpp  
// compile with: /EHa  
#include <iostream>  
  
using namespace std;  
void SEHFunc( void );  
  
int main() {  
   try {  
      SEHFunc();  
   }  
   catch( ... ) {  
      cout << "Caught a C exception."<< endl;  
   }  
}  
  
void SEHFunc() {  
   __try {  
      int x, y = 0;  
      x = 5 / y;  
   }  
   __finally {  
      cout << "In finally." << endl;  
   }  
}  
```  
  
```Output  
In finally.  
Caught a C exception.  
```  
  
##  <a name="_core_c_exception_wrapper_class"></a>C 例外狀況包裝函式類別  
 如上所示的簡單範例，可以攔截 C 例外狀況只要省略符號 (**...**)**攔截**處理常式。 與該例外狀況類型或特性相關的資訊，都不會傳遞至處理常式。 有時候當使用這個方法時，您可能必須定義兩個例外狀況處理模型之間的轉換，如此每個 C 例外狀況才能與特定類別建立關聯。 若要這樣做，您可以定義 C 例外狀況「包裝函式」類別，使用或衍生自這個類別即可將特定類別類型的屬性設為 C 例外狀況。 如此一來，每個 C 例外狀況可由 c + + 處理**攔截**處理常式比個別上述的範例。  
  
 您的包裝函式類別包含的介面可能會包括一些決定例外狀況值的成員函式，而且這些成員函式會存取 C 例外狀況模型所提供的延伸例外狀況內容資訊。 您也可以定義預設的建構函式與接受 `unsigned int` 引數 (以便表示基礎 C 例外狀況) 的建構函式，以及位元複製建構函式。 下列是 C 例外狀況包裝函式類別可能的實作方式：  
  
```  
// exceptions_Exception_Handling_Differences2.cpp  
// compile with: /c  
class SE_Exception {  
private:  
   SE_Exception() {}  
   SE_Exception( SE_Exception& ) {}  
   unsigned int nSE;  
public:  
   SE_Exception( unsigned int n ) : nSE( n ) {}  
   ~SE_Exception() {}  
   unsigned int getSeNumber() {  
      return nSE;  
   }  
};  
  
```  
  
 若要使用這個類別，您必須安裝內部例外狀況處理機制在每次擲回 C 例外狀況時呼叫的自訂 C 例外狀況轉譯函式。 內轉譯函式，您可以擲回任何類型的例外狀況 (可能是`SE_Exception`類型或類別類型衍生自`SE_Exception`)，可以攔截適當的比對 c + +**攔截**處理常式。 轉譯函式可以單純傳回，表示並未處理例外狀況。 如果轉譯函式自行引發 C 例外狀況，[終止](../c-runtime-library/reference/terminate-crt.md)呼叫。  
  
 若要指定自訂轉譯函式，呼叫[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)函式以轉譯函式做為其單一引數的名稱。 您撰寫的轉譯函式呼叫一次，已經在堆疊上的每個函式引動過程**再試一次**區塊。 沒有預設轉譯函式。如果您未指定藉由呼叫其中一個`_set_se_translator`，省略符號可能只會攔截 C 例外狀況**攔截**處理常式。  
  
## <a name="example"></a>範例  
 例如，下列程式碼會安裝自訂轉譯函式，然後引發由 `SE_Exception` 類別包裝的 C 例外狀況：  
  
```  
// exceptions_Exception_Handling_Differences3.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <eh.h>  
#include <windows.h>  
  
class SE_Exception {  
private:  
   SE_Exception() {}  
   unsigned int nSE;  
  
public:  
   SE_Exception( SE_Exception& e) : nSE(e.nSE) {}  
   SE_Exception(unsigned int n) : nSE(n) {}  
   ~SE_Exception() {}  
   unsigned int getSeNumber() { return nSE; }  
};  
  
void SEFunc() {  
   __try {  
      int x, y = 0;  
      x = 5 / y;  
    }  
    __finally {  
      printf_s( "In finally\n" );  
   }  
}  
  
void trans_func( unsigned int u, _EXCEPTION_POINTERS* pExp ) {  
   printf_s( "In trans_func.\n" );  
   throw SE_Exception( u );  
}  
  
int main() {  
   _set_se_translator( trans_func );  
    try {  
      SEFunc();  
    }  
    catch( SE_Exception e ) {  
      printf_s( "Caught a __try exception with SE_Exception.\n" );  
      printf_s( "nSE = 0x%x\n", e.getSeNumber() );  
    }  
}  
```  
  
```Output  
In trans_func.  
In finally  
Caught a __try exception with SE_Exception.  
nSE = 0xc0000094  
```  
  
## <a name="see-also"></a>另請參閱  
 [混合 C (結構化) 和 C++ 例外狀況](../cpp/mixing-c-structured-and-cpp-exceptions.md)