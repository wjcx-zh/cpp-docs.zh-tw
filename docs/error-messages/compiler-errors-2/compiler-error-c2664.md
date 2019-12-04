---
title: 編譯器錯誤 C2664
ms.date: 11/04/2016
f1_keywords:
- C2664
helpviewer_keywords:
- C2664
ms.assetid: 3595d66e-cf87-4fda-a896-c0cd81f95db4
ms.openlocfilehash: 93bdac489dea0356ce3da3298cd8ed6bcb6f623c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756002"
---
# <a name="compiler-error-c2664"></a>編譯器錯誤 C2664

'function': 無法將引數 n 從 'type1' 轉換成 'type2'

如果您建立了類別的執行個體，並嘗試在標記了 `explicit` 關鍵字的建構函式上進行隱含轉換，則可能會發生這個參數轉換問題。 如需明確轉換的詳細資訊，請參閱[使用者定義型別轉換](../../cpp/user-defined-type-conversions-cpp.md)。

如果將暫存物件傳遞至採用物件參考做為參數的函式，則該參考必須是 `const` 參考。

如果函式收到的參數不屬於函式預期的類型，則會使用適當的建構函式建立暫存物件。 之後，會將此暫存物件傳遞至函式上。 在這種情形，此暫存物件被用來初始化參考。 在舊版的語言中，所有參考都可以由暫存物件進行初始化。

若要修正 C2664，

- 重新檢查給定函式的原型 (Prototype)，並修正錯誤訊息中所指出的引數。

- 若有必要，請提供一明確轉換。

如果類別將成員隱藏在它的基底類別其中一個之內，也可能會產生 C2664。

如需詳細資訊，請參閱[如何：將 System：： String 轉換成 wchar_t * 或 char\*](../../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)。

## <a name="example"></a>範例

下列範例會產生 C2664，並示範如何修正此問題。

```cpp
// C2664.cpp
// C2664
struct A {
   void f(int i) {};
};

struct B : public A {
   // To fix, uncomment the following line.
   // using A::f;
   void f(A a) {};
};

int main() {
   B b;
   int i = 1;
   b.f(i);   // B::F hides A::f Uncomment the using declaration in B.
}
```

## <a name="example"></a>範例

此範例也會產生 C2664，並示範如何修正此問題。

```cpp
// C2664b.cpp
// C2664 expected
struct A {
   // To fix, uncomment the following line.
   // A(int i){}
};

void func( int, A ) {}

int main() {
   func( 1, 1 );   // No conversion from int to A.
}
```

## <a name="example"></a>範例

下一個範例將使用字串常值呼叫 `Test` 來示範 C2664，並示範如何修正此問題。 因為參數是 `szString` 參考，所以必須經由適當的建構函式來建立物件。 產生的結果是一個無法被用來初始化參考的暫存物件。

```cpp
// C2664c.cpp
// compile with: /EHsc
// C2664 expected
#include <iostream>
#include <string.h>
using namespace std;

class szString {
   int slen;
   char *str;

public:
   szString(const char *);
   int len() const {
      return slen;
   }
};

// Simple reference cannot bind to temp var.
void Test(szString &a) {}

// To fix, uncomment the following line.
// void Test(const szString &a) {}

szString::szString(const char * newstr) : slen(0), str(NULL) {
   slen=strlen(newstr);
   str = new char[slen + 1];
   if (str)
      strcpy_s(str, (slen + 1), newstr);
}

int main() {
   Test("hello");
}
```

## <a name="example"></a>範例

編譯器會強制執行套用 `const` 的 C++ 標準需求。 此範例會產生 C2664：

```cpp
// C2664d.cpp
// C2664 expected
#include <windows.h>

void func1(LPCSTR &s)
{

}

void func2(LPSTR &s)
{
   func1(s);
}

int main()
{
   return 0;
}
```

## <a name="example"></a>範例

以下是一個會產生 C2664 的比較複雜狀況，包含其修正指示：

```cpp
// C2664e.cpp
// compile with: /EHsc
// C2664 expected
#define _INTL
#include <locale>
#include <iostream>

using namespace std;
#define LEN 90

int main( ) {
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));

   // To fix, delete the following line.
   char* pszNext;

   // To fix, uncomment the following line.
   // const char* pszNext;

   wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).in( state,
      pszExt, &pszExt[strlen(pszExt)], pszNext,
      pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   // See earlier comment.
      pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error) ?
                       L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;

   exit(-1);
}
```

## <a name="example"></a>範例

列舉變數未轉換為其基礎類型，而得以滿足函式呼叫。 如需詳細資訊，請參閱[enum class](../../extensions/enum-class-cpp-component-extensions.md)。 下列範例會產生 C2664，並示範如何修正此問題。

```cpp
// C2664f.cpp
// compile with: /clr
using namespace System;
public enum class A : Char {
   None = 0,
   NonSilent = 1,
};

void Test(Char c) {}

int main() {
   A aa = A::None;
   Test(aa);   // C2664
   Test(Char(aa));   // OK - fix by using a conversion cast
}
```

## <a name="example"></a>範例

midl 編譯器中的 Bug 會造成將 wchar_t 類型做為類型程式庫中不帶正負號的短整數發出。 若要解決這項錯誤，請轉換 C++ 原始程式碼中的類型，或是將類型定義為 idl 檔中的字串。

```
// C2664g.idl
import "prsht.idl";

[ object, uuid(8402B8F1-BF7F-4B49-92D4-C2B9DF4543E9) ]

interface IMyObj1 : IUnknown {
   HRESULT  teststr([in, string] wchar_t *wstr);
   HRESULT  testarr([in, size_is(len)] wchar_t wstr[], [in] int len);
   HRESULT  testbstr([in] BSTR bstr);
};

[  uuid(44463307-CBFC-47A6-8B4F-13CD0A83B436) ]
library myproj1 {
   [  version(1.0), uuid(D8622C12-5448-42B8-8F0E-E3AD6B8470C1) ]
   coclass CMyObj1 { interface IMyObj1; };
}
```

從 Visual C++ 6.0 將程式碼移植到以後版本時，也會使用 `wchar_t` 引發 C2664。 在 Visual C++ 6.0 (含) 以前版本中，`wchar_t` 是 `typedef` 的 `unsigned short`，因此可隱含轉換為該類型。 在 Visual C++ 6.0 之後，`wchar_t` 是它本身的內建類型，如同 C++ 標準中所指定，而且不再能夠隱含轉換為 `unsigned short`。 請參閱[/zc： wchar_t （Wchar_t 是原生類型）](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

## <a name="example"></a>範例

下列範例會產生 C2664，並示範如何修正此問題。

```cpp
// C2664h.cpp
#import "C2664g.tlb"
using namespace myproj1;

int main() {
   IMyObj1Ptr ptr;

   wchar_t * mybuff = 0;
   BSTR bstr = 0;
   int len;
   ptr->teststr(mybuff);
   ptr->testbstr(bstr);
   ptr->testarr(mybuff, len);   // C2664
   ptr->testarr((unsigned short *)mybuff, len);   // OK - Fix by using a cast
}
```

## <a name="example"></a>範例

如果編譯器無法減少樣板引數，也會造成 C2664。

```cpp
// C2664i.cpp
#include <stdio.h>
template <class T, int iType=0>
class CTypedImg {
public:
   CTypedImg() {}
   void run() {}

   operator CTypedImg<T>& () {
      return *((CTypedImg<T>*)this);
    }
};

template <class t1>
void test(CTypedImg<t1>& myarg) {
   myarg.run();
}

int main() {
   CTypedImg<float,2> img;

   test((CTypedImg<float>&)img);   // OK
   test<float>(img);   // OK
   test(img);   // C2664 - qualify as above to fix
}
```
