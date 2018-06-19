---
title: is_placeholder 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- functional/std::is_placeholder
dev_langs:
- C++
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b577803f766d8f5cafa054e84b5b7ec0f152480b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852236"
---
# <a name="isplaceholder-class"></a>is_placeholder 類別

測試類型是否是預留位置。

## <a name="syntax"></a>語法

結構 is_placeholder {靜態 const int 值;};

## <a name="remarks"></a>備註

如果類型 `Ty` 不是預留位置，常數值 `value` 就會是 0；否則其值會是它所繫結之函式呼叫引數的位置。 您可以使用它來判斷第 N 個預留位置 `_N` 的值 `N`。

## <a name="example"></a>範例

```cpp
// std__functional__is_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

using namespace std::placeholders;

template<class Expr>
void test_for_placeholder(const Expr&)
{
    std::cout << std::is_placeholder<Expr>::value << std::endl;
}

int main()
{
    test_for_placeholder(3.0);
    test_for_placeholder(_3);

    return (0);
}
```

```Output
0
3
```

## <a name="requirements"></a>需求

**標頭：**\<functional>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[_1 物件](../standard-library/1-object.md)<br/>
