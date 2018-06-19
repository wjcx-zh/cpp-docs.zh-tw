---
title: __func__ |Microsoft 文件
ms.custom: ''
ms.date: 10/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __func__
dev_langs:
- C++
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d78a249fe5b111c17c29895edcdc3fa5ba2f27a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413589"
---
# <a name="func"></a>__func__

**(C + + 11)** 預先定義的識別項&#95; &#95;func&#95; &#95;隱含定義為字串，其中包含封入函式的非限定和未修飾名稱。 &#95;&#95;func&#95; &#95; c + + 標準所託管，而且不是 Microsoft 擴充功能。

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