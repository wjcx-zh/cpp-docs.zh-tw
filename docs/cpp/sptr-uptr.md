---
title: __sptr、__uptr
ms.date: 10/10/2018
f1_keywords:
- __uptr_cpp
- __sptr_cpp
- __uptr
- __sptr
- _uptr
- _sptr
helpviewer_keywords:
- __sptr modifier
- __uptr modifier
ms.assetid: c7f5f3b2-9106-4a0b-a6de-d1588ab153ed
ms.openlocfilehash: 957f744ca6c5a7be807c1dc68fcd2b602b72300e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330955"
---
# <a name="sptr-uptr"></a>__sptr、__uptr

**Microsoft 專屬**

使用 **__sptr**或是 **__uptr**修飾詞指定編譯器如何將 32 位元指標轉換為 64 位元指標在 32 位元指標宣告。 例如，將 32 位元指標指派給 64 位元指標變數，或在 64 位元平台取值時，就會轉換 32 位元指標。

有關 64 位元平台支援的 Microsoft 文件有時會將 32 位元指標的最高有效位元稱為正負號位元。 根據預設，編譯器會使用正負號擴充項目將 32 位元指標轉換為 64 位元指標。 也就是說，64 位元指標的最低有效 32 位元設為 32 位元指標的值，而最高有效 32 位元則設為 32 位元指標的正負號位元的值。 如果正負號位元是 0，此類轉換會產生正確的結果，如果正負號位元是 1，則不會產生正確結果。 例如，32 位元位址 0x7FFFFFFF 會產生相等的 64 位元位址 0x000000007FFFFFFF，但會將 32 位元位址 0x80000000 錯誤地變更為 0xFFFFFFFF80000000。

**__Sptr**，或帶正負號指標修飾詞可讓您指定指標轉換的 32 位元指標的正負號位元設為 64 位元指標的最大顯著性位元。 **__Uptr**，或轉換設定為零的最大顯著性位元不帶正負號的指標修飾詞指定。 下列宣告顯示 **__sptr**並 **__uptr**搭配兩個不合格指標修飾詞，以限定的兩個指標[__ptr32](../cpp/ptr32-ptr64.md)型別和函式參數。

```cpp
int * __sptr psp;
int * __uptr pup;
int * __ptr32 __sptr psp32;
int * __ptr32 __uptr pup32;
void MyFunction(char * __uptr __ptr32 myValue);
```

使用 **__sptr**並 **__uptr**修飾詞搭配指標宣告。 中的位置使用修飾詞[指標類型限定詞](../c-language/pointer-declarations.md)，表示修飾詞必須在星號。 您不能使用修飾詞搭配[成員的指標](../cpp/pointers-to-members.md)。 修飾詞不影響非指標宣告。

為了與舊版中，相容性 **_sptr**並 **_uptr**同義 **__sptr**和 **__uptr**除非編譯器選項[/Za\(停用語言擴充功能)](../build/reference/za-ze-disable-language-extensions.md)指定。

## <a name="example"></a>範例

下列範例宣告使用的 32 位元指標 **__sptr**並 **__uptr**修飾詞，將每個 32 位元指標指派給 64 位元指標變數，並接著會顯示每個 64 位的十六進位值位元指標。 此範例是以原生 64 位元編譯器編譯，並且在 64 位元平台上執行。

```cpp
// sptr_uptr.cpp
// processor: x64
#include "stdio.h"

int main()
{
    void *        __ptr64 p64;
    void *        __ptr32 p32d; //default signed pointer
    void * __sptr __ptr32 p32s; //explicit signed pointer
    void * __uptr __ptr32 p32u; //explicit unsigned pointer

// Set the 32-bit pointers to a value whose sign bit is 1.
    p32d = reinterpret_cast<void *>(0x87654321);
    p32s = p32d;
    p32u = p32d;

// The printf() function automatically displays leading zeroes with each 32-bit pointer. These are unrelated
// to the __sptr and __uptr modifiers.
    printf("Display each 32-bit pointer (as an unsigned 64-bit pointer):\n");
    printf("p32d:       %p\n", p32d);
    printf("p32s:       %p\n", p32s);
    printf("p32u:       %p\n", p32u);

    printf("\nDisplay the 64-bit pointer created from each 32-bit pointer:\n");
    p64 = p32d;
    printf("p32d: p64 = %p\n", p64);
    p64 = p32s;
    printf("p32s: p64 = %p\n", p64);
    p64 = p32u;
    printf("p32u: p64 = %p\n", p64);
    return 0;
}
```

```Output
Display each 32-bit pointer (as an unsigned 64-bit pointer):
p32d:       0000000087654321
p32s:       0000000087654321
p32u:       0000000087654321

Display the 64-bit pointer created from each 32-bit pointer:
p32d: p64 = FFFFFFFF87654321
p32s: p64 = FFFFFFFF87654321
p32u: p64 = 0000000087654321
```

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[Microsoft 專有的修飾詞](../cpp/microsoft-specific-modifiers.md)