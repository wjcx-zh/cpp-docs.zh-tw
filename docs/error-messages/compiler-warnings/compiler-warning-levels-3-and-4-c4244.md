---
title: 編譯器警告 (層級 3 和 4) C4244
ms.date: 11/04/2016
ms.assetid: f116bb09-c479-4b4e-a647-fe629a1383f6
ms.openlocfilehash: a12bee4591df8a7a952dc741c4b26c637bb5256c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991081"
---
# <a name="compiler-warning-levels-3-and-4-c4244"></a>編譯器警告 (層級 3 和 4) C4244

'conversion'：將 'type1' 轉換為 'type2'，資料可能遺失

整數類型會轉換為較小的整數類型。 如果*type1*是 `int` 且*type2*小於 `int`，這就是層級4警告。 否則，它是層級3（將類型的值[__int64](../../cpp/int8-int16-int32-int64.md)指派給類型 `unsigned int`的變數）。 資料可能會遺失。

如果出現 C4244，您應變更程式以使用相容的類型，或在您的程式碼中加入某些邏輯，以確保可能值的範圍一定會與您所使用的類型相容。

C4244 也可以在層級2引發;如需詳細資訊，請參閱[編譯器警告（層級2） C4244](../../error-messages/compiler-warnings/compiler-warning-level-2-c4244.md) 。

轉換可能會因為隱含轉換而發生問題。

下列範例會產生 C4244：

```cpp
// C4244_level4.cpp
// compile with: /W4
int aa;
unsigned short bb;
int main() {
   int b = 0, c = 0;
   short a = b + c;   // C4244

   bb += c;   // C4244
   bb = bb + c;   // C4244
   bb += (unsigned short)aa;   // C4244
   bb = bb + (unsigned short)aa;   // OK
}
```

如需詳細資訊，請參閱[一般算術轉換](../../c-language/usual-arithmetic-conversions.md)。

```cpp
// C4244_level3.cpp
// compile with: /W3
int main() {
   __int64 i = 8;
   unsigned int ii = i;   // C4244
}
```

為 64 位元目標建置程式碼時，可能會發生為 32 位元目標建置時不會產生的警告 C4244。 以指標之間的差異為例，32 位元平台上的是 32 位元數量，但 64 位元平台上的會是 64 位元數量。

下列範例會在進行 64 位元目標的編譯時產生 C4244：

```cpp
// C4244_level3_b.cpp
// compile with: /W3
int main() {
   char* p1 = 0;
   char* p2 = 0;
   int x = p2 - p1;   // C4244
}
```
