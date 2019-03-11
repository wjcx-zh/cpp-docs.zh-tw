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
ms.openlocfilehash: 984a20d701b159820a94483fe9d3743f015b71f6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741957"
---
# <a name="double-thunking-c"></a>Double Thunking (C++)

Double thunking 指的是效能的您可能會遇到 Visual c + + managed 函式，其中程式執行受管理的內容呼叫的函式呼叫才能夠呼叫 managed 函式呼叫函式的原生進入點時損失。 本主題討論 double thunking 的發生位置，並避免可改善效能。

## <a name="remarks"></a>備註

根據預設，當使用編譯 **/clr**，managed 函式的定義可讓編譯器產生的 managed 的進入點和原生進入點。 這可讓受管理的函式，呼叫從原生和 managed 呼叫站台。 不過，當原生進入點存在時，它可以是函式所有呼叫的進入點。 如果呼叫的函式為 managed，原生進入點會接著呼叫 managed 的進入點。 作用中，兩個呼叫會叫用所需的函式 (因此，double thunking)。 例如，虛擬函式一律會呼叫透過原生進入點。

一個解決方式是告知編譯器不要將產生的受管理的函式的原生進入點，呼叫此函數會只從受管理的內容中，使用[__clrcall](../cpp/clrcall.md)呼叫慣例。

同樣地，如果您匯出 ([dllexport、 dllimport](../cpp/dllexport-dllimport.md)) 的受管理的函式，會產生原生進入點和任何匯入，並呼叫該函式的函式會呼叫透過原生進入點。 若要避免 double thunking，在此情況下，不使用原生的匯出/匯入語意;只要參考的中繼資料，透過`#using`(請參閱 < [#using 指示詞](../preprocessor/hash-using-directive-cpp.md))。

編譯器已更新為減少不必要的 double thunking。 比方說，managed 類型 （包括傳回型別） 的簽章中具有的任何函式會隱含地標示為`__clrcall`。 如需雙 thunk 排除的詳細資訊，請參閱[ https://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx ](https://msdn.microsoft.com/msdnmag/issues/05/01/COptimizations/default.aspx)。

## <a name="example"></a>範例

### <a name="description"></a>描述

下列範例會示範 double thunking。 原生編譯時 (不含 **/clr**) 中的虛擬函式呼叫`main`會產生一個呼叫`T`的複製建構函式和解構函式呼叫。 類似的行為在虛擬函式宣告與時達成 **/clr**和`__clrcall`。 不過，只編譯時 **/clr**、 函式呼叫產生複製建構函式呼叫，但不是會因為原生 managed 的 thunk 的複製建構函式的另一個呼叫。

### <a name="code"></a>程式碼

```
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

先前的範例所示範 double thunking 的存在。 此範例會示範其效果。 `for`迴圈呼叫虛擬函式和程式的報表執行時間。 與編譯程式時，最慢的時間會回報 **/clr**。 而不需要進行編譯時，會報告的最快時間 **/clr**則宣告虛擬函式`__clrcall`。

### <a name="code"></a>程式碼

```
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

[混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)
