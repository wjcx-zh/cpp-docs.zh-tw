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
ms.openlocfilehash: 24c3a7f85c4ea05c38f3ab1d3f637ea0ab24d4c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363750"
---
# <a name="based-pointers-c"></a>Based 指標 (C++)

**__based**關鍵字允許您根據指標(與現有指標偏移的指標)聲明指標。 **__based**關鍵字特定於Microsoft。

## <a name="syntax"></a>語法

```
type __based( base ) declarator
```

## <a name="remarks"></a>備註

基於指標位址的指標是 **__based**關鍵字的唯一形式,在32位或64位編譯中有效。 對於 Microsoft 32 位元 C/C++ 編譯器，基底指標是來自 32 位元指標基底的 32 位元位移。 在 64 位元環境中保留了一個類似的限制，其中基底指標是來自 64 位元基底的 64 位元位移。

以指標為基礎之指標的其中一項用途，就是包含指標的持續性識別項。 以指標為基礎的指標所組成的連結清單可以儲存至磁碟，然後以仍然有效的指標重新載入至記憶體中的另一個位置。 例如：

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
> 包含指標的持久標識符也可以通過使用[記憶體映射檔](/windows/win32/Memory/file-mapping)來完成。

對基底指標取值時，該基底必須透過宣告明確指定或以隱含方式得知。

為了與早期版本相容,**除非**指定編譯器選項[/Za\(禁用語言擴展,](../build/reference/za-ze-disable-language-extensions.md)否則_based是 **__based**的同義詞。

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
