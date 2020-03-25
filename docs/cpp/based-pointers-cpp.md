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
ms.openlocfilehash: f16e9f6582ae846c0c19fc1dcbd86f09baba713e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181391"
---
# <a name="based-pointers-c"></a>Based 指標 (C++)

**__Based**關鍵字可讓您根據指標（從現有指標位移的指標）來宣告指標。 **__Based**關鍵字是 Microsoft 特定的。

## <a name="syntax"></a>語法

```
type __based( base ) declarator
```

## <a name="remarks"></a>備註

以指標位址為基礎的指標是 **__based**關鍵字在32位或64位編譯中有效的唯一形式。 對於 Microsoft 32 位元 C/C++ 編譯器，基底指標是來自 32 位元指標基底的 32 位元位移。 在 64 位元環境中保留了一個類似的限制，其中基底指標是來自 64 位元基底的 64 位元位移。

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
>  保存包含指標的識別碼也可以透過使用[記憶體對應](/windows/win32/Memory/file-mapping)檔案來完成。

對基底指標取值時，該基底必須透過宣告明確指定或以隱含方式得知。

為了與舊版相容，除非指定了編譯器選項[/za \(停用語言擴充功能）](../build/reference/za-ze-disable-language-extensions.md) ，否則 **_based**是 **__based**的同義字。

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
