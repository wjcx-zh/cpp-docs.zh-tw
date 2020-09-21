---
title: 編譯器錯誤 C2660
ms.date: 11/04/2016
f1_keywords:
- C2660
helpviewer_keywords:
- C2660
ms.assetid: 2e01a1db-4f00-4df6-a04d-cb6f70a6922b
ms.openlocfilehash: 179cdc6379fd26f5acd436d5ca6cacc08df8dce3
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743239"
---
# <a name="compiler-error-c2660"></a>編譯器錯誤 C2660

' function '：函數不採用數位參數

使用不正確的參數數目來呼叫函數。

如果您不小心呼叫 Windows API 函式，而不是相同名稱的 MFC 成員函式，就會發生 C2660。 若要解決此問題：

- 調整函式呼叫，以符合成員函式呼叫的格式。

- 使用範圍解析運算子 (`::`) ，告訴編譯器在全域命名空間中搜尋函式名稱。

## <a name="examples"></a>範例

下列範例會產生 C2660。

```cpp
// C2660.cpp
void func( int, int ) {}

int main() {
   func( 1 );   // C2660 func( int ) not declared
   func( 1, 0 );   // OK
}
```

如果您嘗試直接呼叫 managed 類型的 Dispose 方法，也可能會發生 C2660。 如需詳細資訊，請參閱「 [析構函數」和](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)「完成項」。 下列範例會產生 C2660。

```cpp
// C2660_a.cpp
// compile with: /clr
using namespace System;
using namespace System::Threading;

void CheckStatus( Object^ stateInfo ) {}

int main() {
   ManualResetEvent^ event = gcnew ManualResetEvent( false );
   TimerCallback^ timerDelegate = gcnew TimerCallback( &CheckStatus );
   Timer^ stateTimer = gcnew Timer( timerDelegate, event, 1000, 250 );

   stateTimer->Dispose();   // C2660
   stateTimer->~Timer();   // OK
}
```

如果衍生類別隱藏函式，就會發生 C2660。

```cpp
// C2660b.cpp
// C2660 expected
#include <stdio.h>

class f {
public:
   void bar() {
      printf_s("in f::bar\n");
    }
};

class f2 : public f {
public:
   void bar(int i){printf("in f2::bar\n");}
   // Uncomment the following line to resolve.
   // using f::bar;   // - using declaration added
   // or
   // void bar(){__super::bar();}
};

int main() {
   f2 fObject;
   fObject.bar();
}
```

如果您不正確地叫用索引屬性，則可能會發生 C2660。

```cpp
// C2660c.cpp
// compile with: /clr
ref class X {
   double d;
public:
   X() : d(1.9) {}
   property double MyProp[] {
      double get(int i) {
         return d;
      }
   }   // end MyProp definition
};

int main() {
   X ^ MyX = gcnew X();
   System::Console::WriteLine(MyX->MyProp(1));   // C2660
   System::Console::WriteLine(MyX->MyProp[1]);   // OK
}
```

如果您不正確地叫用索引屬性，則可能會發生 C2660。

```cpp
// C2660d.cpp
// compile with: /clr
ref class A{
public:
   property int default[int,int] {
      int get(int a, int b) {
         return a + b;
      }
   }
};

int main() {
   A^ a = gcnew A;
   int x = a[3][5];   // C2660
   int x2 = a[3,5];   // OK
}
```

如果您在樣板類別中定義 new 運算子，但 new 運算子會建立其型別不是封入類型的物件，就會發生 C2660。

```cpp
// C2660e.cpp
// compile with: /c
#include <malloc.h>

template <class T> class CA {
private:
    static T** line;
   void* operator new (size_t, int i) {
      return 0;
   }
   void operator delete(void* pMem, int i) {
      free(pMem);
   }

public:
   CA () { new (1) T(); }   // C2660
   // try the following line instead
   // CA () { new (1) CA<int>(); }
};

typedef CA <int> int_CA;

void AAA() {
   int_CA  list;
}
```
