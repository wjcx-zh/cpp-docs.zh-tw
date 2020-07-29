---
title: Double Thunking (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
ms.openlocfilehash: 6b2d3b4415b81dc5a9b7d0e36c154d9ee74b98ee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221480"
---
# <a name="double-thunking-c"></a>Double Thunking (C++)

Double Thunking 指的是當 managed 內容中的函式呼叫呼叫 Visual C++ managed 函式，以及程式執行呼叫函式的原生進入點以呼叫 managed 函式時，您可能會遇到的效能損失。 本主題討論發生雙重 Thunking 的位置，以及如何避免其改善效能。

## <a name="remarks"></a>備註

根據預設，使用 **/clr**進行編譯時，managed 函式的定義會導致編譯器產生 managed 進入點和原生進入點。 這可讓您從原生和 managed 呼叫網站呼叫 managed 函式。 不過，當原生進入點存在時，它可以是對函式之所有呼叫的進入點。 如果呼叫的函式是受管理的，則原生進入點會接著呼叫受管理的進入點。 實際上，必須呼叫兩次，才能叫用函式（因此，雙重 Thunking）。 例如，虛擬函式一律會透過原生進入點呼叫。

其中一個解決方法是告訴編譯器不要產生 managed 函式的原生進入點，該函式只會從 managed 內容呼叫，方法是使用[__clrcall](../cpp/clrcall.md)呼叫慣例。

同樣地，如果您匯出（[dllexport，dllimport](../cpp/dllexport-dllimport.md)） managed 函式，就會產生原生進入點，而匯入和呼叫該函式的任何函式都會透過原生進入點呼叫。 若要避免在這種情況下進行雙重 Thunking，請勿使用原生匯出/匯入的語義;只要透過參考中繼資料 `#using` （請參閱[#using](../preprocessor/hash-using-directive-cpp.md)指示詞）。

編譯器已更新，以減少不必要的雙重 Thunking。 例如，簽章中具有 managed 類型的任何函式（包括傳回類型）都會隱含地標示為 `__clrcall` 。

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例示範雙重 Thunking。 當編譯的原生（不含 **/clr**）時，在中對虛擬函式的呼叫會 `main` 對的「複製」程式和呼叫者發出一個呼叫 `T` 。 使用 **/clr**和宣告虛擬函式時，就會達到類似的行為 `__clrcall` 。 不過，只要使用 **/clr**進行編譯，函式呼叫就會產生對複製的函式的呼叫，但是因為原生到受控的 Thunk，所以有另一個複製函式的呼叫。

### <a name="code"></a>程式碼

```cpp
// double_thunking.cpp
// compile with: /clr
#include <stdio.h>
struct T {
   T() {
      puts(__FUNCSIG__);
   }

   T(const T&) {
      puts(__FUNCSIG__);
   }

   ~T() {
      puts(__FUNCSIG__);
   }

   T& operator=(const T&) {
      puts(__FUNCSIG__);
      return *this;
   }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;

   printf("calling struct S\n");
   pS->f(t);
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>範例輸出

```
__thiscall T::T(void)
calling struct S
__thiscall T::T(const struct T &)
__thiscall T::T(const struct T &)
__thiscall T::~T(void)
__thiscall T::~T(void)
after calling struct S
__thiscall T::~T(void)
```

## <a name="example"></a>範例

### <a name="description"></a>描述

先前的範例示範了 double Thunking 的存在。 這個範例會顯示它的效果。 **`for`** 迴圈會呼叫虛擬函式，而程式會報告執行時間。 以 **/clr**編譯器時，會回報最慢的時間。 不使用 **/clr**進行編譯時，或如果以宣告虛擬函式，會回報最快的時間 `__clrcall` 。

### <a name="code"></a>程式碼

```cpp
// double_thunking_2.cpp
// compile with: /clr
#include <time.h>
#include <stdio.h>

#pragma unmanaged
struct T {
   T() {}
   T(const T&) {}
   ~T() {}
   T& operator=(const T&) { return *this; }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;
   clock_t start, finish;
   double  duration;
   start = clock();

   for ( int i = 0 ; i < 1000000 ; i++ )
      pS->f(t);

   finish = clock();
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);
   printf( "%2.1f seconds\n", duration );
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>範例輸出

```
4.2 seconds
after calling struct S
```

## <a name="see-also"></a>另請參閱

[混合（原生和 Managed）元件](../dotnet/mixed-native-and-managed-assemblies.md)
