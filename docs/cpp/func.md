---
title: __func__
ms.date: 10/19/2017
f1_keywords:
- __func__
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
ms.openlocfilehash: 8e94caffe120c325478d8b4f24c1915a516d69f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179818"
---
# <a name="__func__"></a>__func__

**（C + + 11）** 預先定義的&#95; &#95;識別碼&#95; &#95; func 會以隱含方式定義為字串，其中包含封入函式的不合格和未名稱。 &#95;&#95;func&#95; &#95;是由C++標準強制的，而且不是 Microsoft 擴充功能。

## <a name="syntax"></a>語法

```cpp
__func__
```

## <a name="return-value"></a>傳回值

傳回包含函式名稱之以 null 結束的 const char 字元陣列。

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
