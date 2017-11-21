---
title: "__func__ |Microsoft 文件"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __func__
dev_langs: C++
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 89a3f569a54c035ddb3f4a9ccc17ab5dfe919d0d
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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