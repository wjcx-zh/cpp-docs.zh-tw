---
title: 編譯器警告（層級1） C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: 8bdd16f5c3182e4217e195475bdb4a9a0f60fa6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164114"
---
# <a name="compiler-warning-level-1-c4067"></a>編譯器警告（層級1） C4067

> 預處理器指示詞後面有未預期的標記-必須是分行符號

## <a name="remarks"></a>備註

編譯器在預處理器指示詞之後找到並略過額外的字元。 這可能是因為任何未預期的字元所造成，但常見的原因是指示詞之後的分號不會被造成。 批註不會造成此警告。 **/Za**編譯器選項會針對比預設設定更多的預處理器指示詞啟用此警告。

## <a name="example"></a>範例

```cpp
// C4067a.cpp
// compile with: cl /EHsc /DX /W1 /Za C4067a.cpp
#include <iostream>
#include <string> s     // C4067
#if defined(X);         // C4067
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif;                 // C4067 only under /Za
int main()
{
    std::cout << s << std::endl;
}
```

若要解決這個警告，請刪除不孤立的字元，或將它們移到批註區塊中。 藉由移除 **/za**編譯器選項，可能會停用某些 C4067 警告。

```cpp
// C4067b.cpp
// compile with: cl /EHsc /DX /W1 C4067b.cpp
#include <iostream>
#include <string>
#if defined(X)
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif
int main()
{
    std::cout << s << std::endl;
}
```
