---
title: "__func__ |Microsoft 文件"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __func__
dev_langs:
- C++
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ddb92e84545de175734550eca8911590fa1d539
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="func"></a>__函式__

**(C + + 11)**預先定義的識別項 #95; &#95; func &#95; &#95; 隱含定義為字串，其中包含封入函式的非限定和未修飾名稱。 &#95; &#95; func &#95; &#95;c + + 標準所託管，而且不是 Microsoft 擴充功能。

## <a name="syntax"></a>語法

```cpp
__func__
```

## <a name="return-value"></a>傳回值

傳回以 null 終止 const char 的字元陣列，其中包含函式名稱。

## <a name="example"></a>範例

```cpp
#include <string>
#include <iostream>

namespace Test
{
    struct Foo
    {
        static void DoSomething(int i, std::string s)
        {
           std::cout << __func__ << std::endl; // Output: DoSomething
        }
    };
}

int main()
{
    Test::Foo::DoSomething(42, "Hello");

    return 0;
}
```

## <a name="requirements"></a>需求

C++11