---
title: pack
ms.date: 12/17/2018
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: bf1ae81184d53dd271f63c26e8f9a52a6410b232
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038443"
---
# <a name="pack"></a>pack
指定結構、等位及類別成員的封裝對齊。

## <a name="syntax"></a>語法

```
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )
```

### <a name="parameters"></a>參數

**顯示**<br/>
（選擇性）顯示目前的封裝對齊的位元組值。 此值是透過警告訊息顯示。

**push**<br/>
（選擇性）推送目前的封裝對齊值的內部編譯器堆疊和目前的封裝對齊值的集合*n*。 如果*n*未指定，目前的封裝對齊值推入。

**pop**<br/>
（選擇性）從內部編譯器堆疊頂端移除記錄。 如果*n*不利用指定**pop**，然後在堆疊頂端產生的記錄相關聯的封裝值即新的封裝對齊值。 如果*n*指定，例如`#pragma pack(pop, 16)`， *n*會變成新的封裝對齊值。 如果快顯*識別碼*，例如`#pragma pack(pop, r1)`，然後在堆疊上的所有記錄會都彈出的記錄直到*識別碼*找到。 會快顯該記錄，且與堆疊頂端產生的記錄關聯的封裝值即為新的封裝對齊值。 如果快顯*識別碼*，會中找不到任何記錄在堆疊上，則**pop**會被忽略。

*識別項*<br/>
（選擇性）當搭配*推播*，將名稱指派給內部編譯器堆疊上的記錄。 當搭配**pop**，會將記錄推出內部堆疊，直到*識別項*已移除; 如果*識別碼*找不到在內部堆疊上，不會推出。

*n*<br/>
（選擇性）指定值，以位元組為單位，用以封裝。 如果編譯器選項[/Zp](../build/reference/zp-struct-member-alignment.md)模組的預設值未設定*n*為 8。 有效值為 1、2、4、8 和 16。 成員的對齊方式會是在可能的界限上的倍數*n*或成員的大小的倍數取其較小。

`#pragma pack(pop, identifier, n)` 未定義。

## <a name="remarks"></a>備註

封裝類別是指將類別的成員交錯放入記憶體中，這可能表示部分或所有的成員能夠在比目標架構的預設對齊還小的界限上對齊。 **組件**資料宣告層級的控制權。 這不同於編譯器選項[/Zp](../build/reference/zp-struct-member-alignment.md)，後者只會提供模組層級的控制。 **組件**會在第一個生效**struct**，**聯集**，或**類別**顯示該 pragma 後的宣告。 **組件**具有對定義無作用。 呼叫**pack**沒有引數集*n*編譯器選項中設定的值來`/Zp`。 如果未設定編譯器選項，則預設值為 8。

如果您變更結構的對齊，結構在記憶體中可能不會佔用太多空間，但效能可能會降低，甚至可能會出現硬體所產生的未對齊存取例外狀況。  您可以使用，以修改此例外狀況行為[SetErrorMode](https://msdn.microsoft.com/library/windows/desktop/ms680621)。

如需有關如何修改對齊的詳細資訊，請參閱下列主題：

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [結構對齊範例](../build/x64-software-conventions.md#examples-of-structure-alignment)(x64 專用)

   > [!WARNING]
   > 請注意，在 Visual Studio 2015 和更新版本中，您可以使用標準 alignas 和 alignof 運算子，與可跨編譯器移植的 `__alignof` 和 `declspec( align )` 不同。 C + + 標準無法處理封裝作業，因此您仍然必須使用**組件**（或其他編譯器上對應的延伸模組） 來指定比目標架構的文字大小較小的對齊方式。

## <a name="examples"></a>範例

下列範例示範如何使用**組件**pragma 變更結構的對齊方式。

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

下列範例示範如何使用*推播*， *pop*，並*顯示*語法。

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)