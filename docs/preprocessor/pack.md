---
title: pack pragma
ms.date: 07/22/2020
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: 72f94520516cce2ae36b70795fb29e3d4d8068df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219387"
---
# <a name="pack-pragma"></a>pack pragma

指定結構、聯集和類別成員的封裝對齊方式。

## <a name="syntax"></a>語法

> **`#pragma pack( show )`**\
> **`#pragma pack( push`** [ **`,`** *`identifier`* ] [ **`,`** *`n`* ] **`)`**\
> **`#pragma pack( pop`** [ **`,`** { *`identifier`* | *`n`* } ] **`)`**\
> **`#pragma pack(`** [ *`n`* ] **`)`**

### <a name="parameters"></a>參數

**`show`**\
選擇性顯示封裝對齊的目前位元組值。 此值是透過警告訊息顯示。

**`push`**\
選擇性將目前的封裝對齊值推送到內部編譯器堆疊上，並將目前的封裝對齊值設定為*n*。 如果未指定*n* ，則會推送目前的封裝對齊值。

**`pop`**\
選擇性從內部編譯器堆疊頂端移除記錄。 如果*n*未使用指定 n **`pop`** ，則與堆疊頂端產生的記錄相關聯的封裝值就是新的封裝對齊值。 例如，如果指定*n* ，則 `#pragma pack(pop, 16)` *n*會成為新的封裝對齊值。 例如，如果您使用快顯，則 *`identifier`* `#pragma pack(pop, r1)` 堆疊上的所有記錄都會推出，直到找到具有的記錄為止 *`identifier`* 。 該記錄會隨即推出，而與堆疊頂端找到的記錄相關聯的封裝值，會成為新的封裝對齊值。 如果您使用在 *`identifier`* 堆疊上的任何記錄中找不到的 pop，則 **`pop`** 會忽略。

語句 `#pragma pack (pop, r1, 2)` 相當於 `#pragma pack (pop, r1)` 後面接著 `#pragma pack(2)` 。

*`identifier`*\
選擇性搭配使用時 **`push`** ，會指派名稱給內部編譯器堆疊上的記錄。 搭配使用時 **`pop`** ，會從內部堆疊中取出記錄，直到 *`identifier`* 移除為止。 如果在 *`identifier`* 內部堆疊上找不到，則不會彈出任何內容。

*`n`*\
選擇性指定用於封裝的值（以位元組為單位）。 如果 [`/Zp`](../build/reference/zp-struct-member-alignment.md) 未針對模組設定編譯器選項，則的預設值 *`n`* 為8。 有效值為 1、2、4、8 和 16。 成員的對齊方式位於界限上，也就是的倍數 *`n`* ，或成員大小的倍數（取其較小者）。

## <a name="remarks"></a>備註

若*要封裝類別，請*將其成員直接放在記憶體中彼此的後面。 這可能表示某些或所有成員可以對齊界限，其範圍小於目標架構的預設對齊方式。 **`pack`** 提供資料宣告層級的控制項。 它不同于編譯器選項 [`/Zp`](../build/reference/zp-struct-member-alignment.md) ，它只提供模組層級的控制項。 **pack**會在 **`struct`** **`union`** 出現 pragma 之後的第一個、或宣告生效 **`class`** 。 **`pack`** 對定義沒有影響。 **`pack`** 不使用引數呼叫會將設定 *`n`* 為在編譯器選項中設定的值 **`/Zp`** 。 如果未設定編譯器選項，則 x86、ARM 和 ARM64 的預設值為8。 X64 native 的預設值為16。

如果您變更結構的對齊方式，它可能不會在記憶體中使用太多空間。 不過，您可能會看到效能遺失，或甚至取得硬體產生的未對齊存取例外狀況。 您可以使用來修改這個例外狀況行為 [`SetErrorMode`](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) 。

如需如何修改對齊的詳細資訊，請參閱下列文章：

- [`alignof`](../cpp/alignof-operator.md)

- [`align`](../cpp/align-cpp.md)

- [`__unaligned`](../cpp/unaligned.md)

- [結構對齊範例](../build/x64-software-conventions.md#examples-of-structure-alignment)（x64 專用）

   > [!WARNING]
   > 在 Visual Studio 2015 和更新版本中，您可以使用標準 **`alignas`** 和 **`alignof`** 運算子，不同于 **`__alignof`** 並可 **`__declspec( align )`** 跨編譯器移植。 C + + 標準不會處理封裝，因此您仍然必須使用 **`pack`** （或其他編譯器上的對應延伸模組）來指定比目標架構的文字大小還小的對齊方式。

## <a name="examples"></a>範例

下列範例顯示如何使用 **`pack`** pragma 來變更結構的對齊。

```cpp
// pragma_directives_pack.cpp
#include <stddef.h>
#include <stdio.h>

struct S {
   int i;   // size 4
   short j;   // size 2
   double k;   // size 8
};

#pragma pack(2)
struct T {
   int i;
   short j;
   double k;
};

int main() {
   printf("%zu ", offsetof(S, i));
   printf("%zu ", offsetof(S, j));
   printf("%zu\n", offsetof(S, k));

   printf("%zu ", offsetof(T, i));
   printf("%zu ", offsetof(T, j));
   printf("%zu\n", offsetof(T, k));
}
```

```Output
0 4 8
0 4 6
```

下列範例顯示如何使用*push*、 *pop*和*show*語法。

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810

// pop to the identifier and then set
// the value of the current packing alignment:
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 `__pragma` 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
