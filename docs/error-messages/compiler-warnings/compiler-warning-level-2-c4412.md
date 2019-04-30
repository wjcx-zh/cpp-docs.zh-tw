---
title: 編譯器警告 (層級 2) C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 2c9d50fc3433321c0ca92366a512892212545754
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402433"
---
# <a name="compiler-warning-level-2-c4412"></a>編譯器警告 (層級 2) C4412

> '*函式*': 函式簽章含有類型'*型別*';C++物件都是 unsafe 純程式碼之間傳遞並混合或原生。

## <a name="remarks"></a>備註

**/Clr: pure**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。 如果您有必須是單純的程式碼，我們建議您移植到C#。

編譯器偵測到可能不安全的情況下，可能會導致執行階段錯誤： 正在進行呼叫，從 **/clr: pure**編譯模組已匯入透過 dllimport 和函式簽章的函式包含不安全的類型. 類型為不安全的如果它包含一個成員函式，或為不安全的型別或不安全類型的間接取值的資料成員。

這是因為不同的預設呼叫慣例純粹的和原生程式碼之間的不安全 （或混合原生和 managed）。 當匯入 (透過`dllimport`) 函式匯入 **/clr: pure**編譯時，請確保匯出函式 （尤其是謹慎的編譯相同的簽章中的每個型別宣告差異隱含的呼叫慣例）。

虛擬成員函式是特別容易產生非預期的結果。  不過，即使非虛擬函式應該測試以確保您取得正確的結果。 如果您不確定您會收到正確的結果，您可以忽略此警告。

C4412 預設為關閉。 請參閱[編譯器警告為關閉的預設](../../preprocessor/compiler-warnings-that-are-off-by-default.md)並[dllexport、 dllimport](../../cpp/dllexport-dllimport.md)如需詳細資訊。

若要解決這個警告，移除型別中的所有函式。

## <a name="example"></a>範例

下列範例會產生 C4412。

```cpp
// C4412.cpp
// compile with: /c /W2 /clr:pure
#pragma warning (default : 4412)

struct Unsafe {
   virtual void __cdecl Test();
};

struct Safe {
   int i;
};

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   Unsafe *pUnsafe = func();   // C4412
   // pUnsafe->Test();

   Safe *pSafe = func2();   // OK
}
```

## <a name="example"></a>範例

下列範例會宣告兩種類型的標頭檔。 `Unsafe`類型是不安全，因為它有成員函式。

```cpp
// C4412.h
struct Unsafe {
   // will be __clrcall if #included in pure compilation
   // defaults to __cdecl in native or mixed mode compilation
   virtual void Test(int * pi);

   // try the following line instead
   // virtual void __cdecl Test(int * pi);
};

struct Safe {
   int i;
};
```

## <a name="example"></a>範例

此範例會匯出函式使用的標頭檔中定義的類型。

```cpp
// C4412_2.cpp
// compile with: /LD
#include "C4412.h"

void Unsafe::Test(int * pi) {
   *pi++;
}

__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }
```

## <a name="example"></a>範例

預設呼叫慣例 **/clr: pure**編譯為不同於原生編譯。  包含在內，C4412.h 時`Test`預設為`__clrcall`。 如果您編譯並執行此程式 (請勿使用 **/c**)，程式將會擲回例外狀況。

下列範例會產生 C4412。

```cpp
// C4412_3.cpp
// compile with: /W2 /clr:pure /c /link C4412_2.lib
#pragma warning (default : 4412)
#include "C4412.h"

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   int n = 7;
   Unsafe *pUnsafe = func();   // C4412
   pUnsafe->Test(&n);

   Safe *pSafe = func2();   // OK
}
```