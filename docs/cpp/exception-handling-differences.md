---
title: 處理結構化例外狀況，在 c + + |Microsoft Docs
ms.custom: ''
ms.date: 08/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48acd13aced14bfd8acbeb4c306a5749010636d7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086030"
---
# <a name="handle-structured-exceptions-in-c"></a>處理 c + + 中的結構化例外狀況

主要的不同 C 結構化例外狀況處理 (SEH) 和 c + + 例外狀況處理時，c + + 例外狀況處理模型是處理類型，而 C 結構化例外狀況處理模型處理例外狀況的一種類型;具體而言，**不帶正負號的 int**。也就是說，C 例外狀況是以不帶正負號的整數值來識別，而 C++ 例外狀況則是以資料類型來識別。 在 C 中引發結構化例外狀況時，每個可能的處理常式會執行篩選條件來檢查 C 例外狀況內容，並決定是否要接受該例外狀況、 將它傳遞給其他處理常式，或忽略它。 C++ 中擲回例外狀況時，它可能是任何類型。

第二個差異是，C 結構化例外狀況處理模型指*非同步*，因為發生一般控制流程的次要例外狀況。 C + + 例外狀況處理機制已完全*同步*，這表示發生只有當在擲回例外狀況。

當您使用[/EHs 或 /EHsc](../build/reference/eh-exception-handling-model.md)編譯器選項、 沒有 c + + 例外狀況處理常式處理結構化例外狀況。 只有處理這些例外狀況 **__catch**結構化例外狀況處理常式或 **__finally**結構化終止處理常式。 如需資訊，請參閱[Structured Exception Handling （C/c + +）](structured-exception-handling-c-cpp.md)。

底下[/EHa](../build/reference/eh-exception-handling-model.md)編譯器選項時，如果在 c + + 程式中引發 C 例外狀況時，它可以處理其相關聯的篩選器的結構化例外狀況處理常式或 c + +**攔截**處理常式，兩者取其較以動態方式准例外狀況內容。 例如，下列 c + + 程式會引發 C 例外狀況，在 c + +**嘗試**內容：

## <a name="example---catch-a-c-exception-in-a-c-catch-block"></a>範例-c + + 中的 Catch C 例外狀況的 catch 區塊

```cpp
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

## <a name="c-exception-wrapper-classes"></a>C 例外狀況包裝函式類別

在如上所示的簡單範例，可以攔截 C 例外狀況只能由省略符號 (**...**)**攔截**處理常式。 與該例外狀況類型或特性相關的資訊，都不會傳遞至處理常式。 雖然這個方法的運作方式，在某些情況下您可能想要定義兩個例外狀況處理模型之間的轉換，使每個 C 例外狀況相關聯的特定類別。 若要這樣做，您可以定義 C 例外狀況「包裝函式」類別，使用或衍生自這個類別即可將特定類別類型的屬性設為 C 例外狀況。 如此一來，每個 C 例外狀況可以分開處理特定的 c + +**攔截**處理常式，而不是全部都放在單一處理常式。

您的包裝函式類別包含的介面可能會包括一些決定例外狀況值的成員函式，而且這些成員函式會存取 C 例外狀況模型所提供的延伸例外狀況內容資訊。 您也可以在定義的預設建構函式和接受的建構函式**不帶正負號的 int** （以提供之基礎 C 例外狀況表示） 的引數，以及位元複製建構函式。 以下是 C 例外狀況包裝函式類別的實作：

```cpp
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

若要使用這個類別，安裝自訂 C 例外狀況轉譯函式所呼叫的處理機制在每次擲回 C 例外狀況的內部例外狀況。 在您的轉譯函式，您可以擲回任何類型的例外狀況 (或許`SE_Exception`類型或類別類型衍生自`SE_Exception`)，就可以攔截適當的比對 c + +**攔截**處理常式。 轉譯函式可以單純傳回，表示並未處理例外狀況。 如果轉譯函式自行引發 C 例外狀況[終止](../c-runtime-library/reference/terminate-crt.md)呼叫。

若要指定自訂轉譯函式，呼叫[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)函式的轉譯函式作為其單一引數名稱。 您撰寫的轉譯函式會呼叫一次有在堆疊上的每個函式引動過程**嘗試**區塊。 沒有預設轉譯函式;如果您未指定藉由呼叫其中一個 **_set_se_translator**，省略符號可能只會攔截 C 例外狀況**攔截**處理常式。

## <a name="example---use-a-custom-translation-function"></a>範例-使用自訂轉譯函式

例如，下列程式碼會安裝自訂轉譯函式，然後引發由 `SE_Exception` 類別包裝的 C 例外狀況：

```cpp
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

[混合 C （結構化） 和 c + + 例外狀況](../cpp/mixing-c-structured-and-cpp-exceptions.md)
