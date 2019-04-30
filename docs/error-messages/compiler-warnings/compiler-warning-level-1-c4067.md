---
title: 編譯器警告 （層級 1） C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: 012866e328433ec9511782c26a39265481ff4940
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386508"
---
# <a name="compiler-warning-level-1-c4067"></a>編譯器警告 （層級 1） C4067

> 未預期的語彙基元下列前置處理器指示詞-必須是新行

## <a name="remarks"></a>備註

編譯器發現，並忽略多餘的字元，前置處理器指示詞後面。 原因可能是任何非預期的字元，但常見的原因是偏離分號指示詞之後。 註解不會導致此警告。 **/Za**編譯器選項可讓這項警告比預設設定的多個前置處理器指示詞。

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

若要解決這個警告，請刪除偏離的字元，或將它們移入註解區塊。 某些 C4067 警告可能會停用，藉由移除 **/Za**編譯器選項。

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