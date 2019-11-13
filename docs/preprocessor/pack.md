---
title: pack pragma
ms.date: 11/11/2019
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: 3572bd0d0b0e8149f527c1c43eca5870783b13a8
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965249"
---
# <a name="pack-pragma"></a>pack pragma

指定結構、聯集和類別成員的封裝對齊方式。

## <a name="syntax"></a>語法

> **#pragma pack （show）** \
> **#pragma pack （push** [ **，** *identifier* ] [ **，** *n* ] **）** \
> **#pragma pack （pop** [ **，** { *identifier* | *n* }] **）** \
> **#pragma pack （** [ *n* ] **）**

### <a name="parameters"></a>參數

**顯示**\
選擇性顯示封裝對齊的目前位元組值。 此值是透過警告訊息顯示。

**推送**\
選擇性將目前的封裝對齊值推送到內部編譯器堆疊上，並將目前的封裝對齊值設定為*n*。 如果未指定*n* ，則會推送目前的封裝對齊值。

**pop**\
選擇性從內部編譯器堆疊頂端移除記錄。 如果未使用**pop**指定*n* ，則與堆疊頂端產生的記錄相關聯的封裝值就是新的封裝對齊值。 例如 `#pragma pack(pop, 16)`，如果指定*n* ，則*n*會變成新的封裝對齊值。 如果您使用*識別碼*（例如 `#pragma pack(pop, r1)`）來結束，則堆疊上的所有記錄都會推出，直到找到具有*識別碼*的記錄為止。 該記錄會隨即推出，而與堆疊頂端產生的記錄相關聯的封裝值即為新的封裝對齊值。 如果您使用在堆疊上的任何記錄中找不到的*識別碼*來快顯，則會忽略**pop** 。 

語句 `#pragma pack (pop, r1, 2)` 相當於後面接著 `#pragma pack(2)`的 `#pragma pack (pop, r1)`。

*識別碼*\
選擇性與**push**搭配使用時，會指派名稱給內部編譯器堆疊上的記錄。 與**pop**搭配使用時，會將內部堆疊的記錄，直到移除*識別碼*為止。 如果在內部堆疊上找不到*識別碼*，則不會彈出任何內容。

*n*\
選擇性指定用於封裝的值（以位元組為單位）。 如果未針對模組設定編譯器選項[/Zp](../build/reference/zp-struct-member-alignment.md) ， *n*的預設值為8。 有效值為 1、2、4、8 和 16。 成員的對齊是在一個界限上，也就是*n*的倍數，或成員大小的倍數，以較小者為准。

## <a name="remarks"></a>備註

若*要封裝類別，請*將其成員直接放在記憶體中彼此的後面。 這可能表示某些或所有成員可以對齊界限，其範圍小於目標架構的預設對齊方式。 **pack**會提供資料宣告層級的控制權。 它與編譯器選項[/Zp](../build/reference/zp-struct-member-alignment.md)不同，後者只會提供模組層級的控制項。 在觀察到 pragma 之後， **pack**會在第一個**結構** **、等**位或**類別**宣告上生效。 **pack**不會影響定義。 沒有引數的呼叫**pack**會將*n*設定為在編譯器選項中設定的值 `/Zp`。 如果未設定編譯器選項，則預設值為8。

如果您變更結構的對齊，結構在記憶體中可能不會佔用太多空間，但效能可能會降低，甚至可能會出現硬體所產生的未對齊存取例外狀況。  您可以使用[SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode)來修改此例外狀況行為。

如需如何修改對齊的詳細資訊，請參閱下列文章：

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [結構對齊範例](../build/x64-software-conventions.md#examples-of-structure-alignment)（x64 專用）

   > [!WARNING]
   > 在 Visual Studio 2015 和更新版本中，您可以使用標準**alignas**和**alignof**運算子，這不同于 `__alignof`，而 `declspec( align )` 可在編譯器間移植。 C++標準不會處理封裝，因此您仍然必須使用**pack** （或其他編譯器上的對應延伸模組）來指定比目標架構的文字大小更小的對齊方式。

## <a name="examples"></a>範例

下列範例顯示如何使用**pack** pragma 來變更結構的對齊。

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

## <a name="see-also"></a>請參閱

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)