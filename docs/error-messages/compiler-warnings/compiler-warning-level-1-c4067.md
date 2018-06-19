---
title: 編譯器警告 （層級 1） C4067 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4067
dev_langs:
- C++
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2ee6b48327e8754f9388e0df8f43009a5be70c97
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255449"
---
# <a name="compiler-warning-level-1-c4067"></a>編譯器警告 （層級 1） C4067

> 未預期的語彙基元下列前置處理器指示詞-必須是新行

## <a name="remarks"></a>備註

編譯器發現，並忽略多餘的字元，前置處理器指示詞後面。 這可能被因未預期的字元，但常見的原因是偏離分號指示詞後。 註解不會導致此警告。 **/Za**編譯器選項可讓這項警告詳細的前置處理器指示詞，比預設設定。

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

若要解決這個警告，刪除偏離的字元，或將它們移入註解區塊。 某些 C4067 警告可能會停用移除 **/Za**編譯器選項。

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