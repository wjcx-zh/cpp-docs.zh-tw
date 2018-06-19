---
title: 編譯器警告 （層級 1） C4305 |Microsoft 文件
ms.custom: ''
ms.date: 1/17/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4305
dev_langs:
- C++
helpviewer_keywords:
- C4305
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7694c511f57b6907227d62f969b61218f836cb14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277819"
---
# <a name="compiler-warning-level-1-c4305"></a>編譯器警告 (層級 1) C4305

> '*內容*': 從截斷'*type1*'to'*type2*'  

## <a name="remarks"></a>備註

值，轉換為較小的類型在初始化期間，或做為建構函式引數，導致遺失資訊時，會發出這個警告。

## <a name="example"></a>範例

這個範例會示範兩種方式，您可能會看到這個警告：

```cpp
// C4305.cpp
// Compile by using: cl /EHsc /W4 C4305.cpp

struct item
{
    item(float) {}
};

int main()
{
    float f = 2.71828;          // C4305 'initializing'
    item i(3.14159);            // C4305 'argument'
    return static_cast<int>(f);
}
```

若要修正此問題，使用正確的類型、 值來初始化，或使用明確轉換成正確的型別。 比方說，使用**float**例如 2.71828f 而不是常值**double** （浮點常值的預設類型） 來初始化**float**變數，或要傳遞給使用建構函式**float**引數。
