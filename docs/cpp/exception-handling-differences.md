---
title: 使用 C++ 處理結構化例外狀況
description: 如何使用C++例外狀況處理模型來處理結構化例外狀況。
ms.date: 09/19/2019
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
ms.openlocfilehash: 0c0e458f576325034d77676d247020adedfa33e5
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158733"
---
# <a name="handle-structured-exceptions-in-c"></a>使用 C++ 處理結構化例外狀況

C 結構化例外狀況處理（SEH）和C++例外狀況處理之間的主要差異C++在於，例外狀況處理模型會處理類型，而 C 結構化例外狀況處理模型則會處理某種類型的例外狀況;具體而言，不**帶正負**號的整數。也就是說，C 例外狀況是以不帶正負號的整數值來識別，而 C++ 例外狀況則是以資料類型來識別。 當 C 中引發了結構化例外狀況時，每個可能的處理常式都會執行一個篩選準則，檢查 C 例外狀況內容並判斷是否接受例外狀況、將它傳遞給其他處理常式，或予以忽略。 C++ 中擲回例外狀況時，它可能是任何類型。

第二個差異是 C 結構化例外狀況處理模型稱為*非同步*，因為例外狀況是在一般控制流程的次要處發生。 C++例外狀況處理機制是完全*同步*的，這表示例外狀況只會在擲回時才會發生。

當您使用[/ehs 或/ehsc](../build/reference/eh-exception-handling-model.md)編譯器選項時，沒有C++任何例外狀況處理常式會處理結構化例外狀況。 這些例外狀況只會由 **__except**結構化例外狀況處理常式或 **__finally**結構化終止處理常式來處理。 如需相關資訊，請參閱[結構化例外C++狀況處理（C/）](structured-exception-handling-c-cpp.md)。

在[/eha](../build/reference/eh-exception-handling-model.md)編譯器選項底下，如果C++程式中引發 C 例外狀況，它可以由結構化例外狀況處理常式與其相關聯的篩選或C++ **catch**處理常式處理，以動態方式接近例外狀況內容. 例如，此範例C++程式會在C++ **try**內容中引發 C 例外狀況：

## <a name="example---catch-a-c-exception-in-a-c-catch-block"></a>範例-攔截C++ catch 區塊中的 C 例外狀況

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

在上述的簡單範例中，C 例外狀況只能由省略號（...）捕捉 **。** **catch**處理常式。 與該例外狀況類型或特性相關的資訊，都不會傳遞至處理常式。 雖然這個方法可行，但在某些情況下，您可能會想要在兩個例外狀況處理模型之間定義轉換，讓每個 C 例外狀況都與特定的類別相關聯。 若要轉換一個，您可以定義 C 例外狀況「包裝函式」類別，這可以用或衍生自，以便將特定類別類型的屬性設為 C 例外狀況。 如此一來，每個 C 例外狀況都可以由特定C++的**catch**處理常式分別處理，而不是在單一處理程式中進行。

您的包裝函式類別包含的介面可能會包括一些決定例外狀況值的成員函式，而且這些成員函式會存取 C 例外狀況模型所提供的延伸例外狀況內容資訊。 您可能也會想要定義預設的函式，以及接受不**帶正負號 int**引數的函式（以提供基礎 C 例外狀況標記法）和位複製的函式。 以下是 C 例外狀況包裝函式類別的可能執行：

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

若要使用這個類別，請在每次擲回 C 例外狀況時，安裝內部例外狀況處理機制所呼叫的自訂 C 例外狀況轉譯函式。 在您的轉譯函式內，您可以擲回任何具`SE_Exception`類型的例外狀況（可能是類型`SE_Exception`或衍生自的類別類型），以便C++由適當的相符 catch 處理常式**攔截**。 轉譯函數可以改為傳回，這表示它未處理例外狀況。 如果轉譯函數本身引發 C 例外狀況，則會呼叫[terminate](../c-runtime-library/reference/terminate-crt.md) 。

若要指定自訂轉譯函式，請呼叫[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)函式，並將您的轉譯函式名稱當做其單一引數。 您撰寫的轉譯函式會針對堆疊上具有**try**區塊的每個函式呼叫呼叫一次。 沒有預設的轉譯函數;如果您未藉由呼叫 **_set_se_translator**來指定它，則 C 例外狀況只能由省略號 catch 處理常式**攔截**。

## <a name="example---use-a-custom-translation-function"></a>範例-使用自訂翻譯函數

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

[混合 C （結構化） C++和例外狀況](../cpp/mixing-c-structured-and-cpp-exceptions.md)
