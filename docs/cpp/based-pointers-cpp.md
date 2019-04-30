---
title: Based 指標 (C++)
ms.date: 10/09/2018
f1_keywords:
- __based
- _based
- __based_cpp
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
ms.openlocfilehash: 771d3ee132e4cd63499fec886ef9f7cd06ec0260
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393957"
---
# <a name="based-pointers-c"></a>Based 指標 (C++)

**Microsoft 專屬**

**__Based**關鍵字可讓您宣告指標 （會從現有指標位移的指標） 為基礎的指標。

## <a name="syntax"></a>語法

```

type __based( base ) declarator
```

## <a name="remarks"></a>備註

指標位址為基礎的指標都是唯一的形式 **__based**關鍵字在 32 位元或 64 位元編譯中有效。 對於 Microsoft 32 位元 C/C++ 編譯器，基底指標是來自 32 位元指標基底的 32 位元位移。 在 64 位元環境中保留了一個類似的限制，其中基底指標是來自 64 位元基底的 64 位元位移。

以指標為基礎之指標的其中一項用途，就是包含指標的持續性識別項。 以指標為基礎的指標所組成的連結清單可以儲存至磁碟，然後以仍然有效的指標重新載入至記憶體中的另一個位置。 例如: 

```cpp
// based_pointers1.cpp
// compile with: /c
void *vpBuffer;
struct llist_t {
   void __based( vpBuffer ) *vpData;
   struct llist_t __based( vpBuffer ) *llNext;
};
```

為指標 `vpBuffer` 所指派的記憶體位址，會在程式稍後的位置中進行配置。 連結清單會重新配置相對於 `vpBuffer` 的值。

> [!NOTE]
>  包含指標的持續性識別項也可藉由使用[記憶體對應檔案](/windows/desktop/Memory/file-mapping)。

對基底指標取值時，該基底必須透過宣告明確指定或以隱含方式得知。

為了與舊版中，相容性 **_based**同義 **__based**除非編譯器選項[/Za\(停用語言擴充功能)](../build/reference/za-ze-disable-language-extensions.md)是指定此項目。

## <a name="example"></a>範例

下列程式碼示範如何變更其基底以變更基底指標。

```cpp
// based_pointers2.cpp
// compile with: /EHsc
#include <iostream>

int a1[] = { 1,2,3 };
int a2[] = { 10,11,12 };
int *pBased;

typedef int __based(pBased) * pBasedPtr;

using namespace std;
int main() {
   pBased = &a1[0];
   pBasedPtr pb = 0;

   cout << *pb << endl;
   cout << *(pb+1) << endl;

   pBased = &a2[0];

   cout << *pb << endl;
   cout << *(pb+1) << endl;
}
```

```Output
1
2
10
11
```

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[alloc_text](../preprocessor/alloc-text.md)