---
title: 針對程式碼分析提示使用 _Analysis_assume
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Analysis_assume
helpviewer_keywords:
- _Analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
ms.openlocfilehash: f427afdcab07b41430a5d4b5fc7f300aa671e30b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503297"
---
# <a name="how-to-specify-additional-code-information-by-using-_analysis_assume"></a>如何：使用 _Analysis_assume 指定其他程式碼資訊

您可以提供適用于 C/c + + 程式碼的程式碼分析工具提示，以協助分析程式並減少警告。 若要提供其他資訊，請使用下列函數：

`_Analysis_assume(`  `expr`  `)`

`expr` -假設評估為 true 的任何運算式。

程式碼分析工具假設運算式所表示的條件在函式出現的點為 true，而且在更改運算式之前保持為 true，例如，藉由指派給變數。

> [!NOTE]
> `_Analysis_assume` 不會影響程式碼優化。 在程式碼分析工具之外， `_Analysis_assume` 定義為無作業。

## <a name="example"></a>範例

下列程式碼會使用 `_Analysis_assume` 來修正程式碼分析警告 [C6388](../code-quality/c6388.md)：

```cpp
#include<windows.h>
#include<codeanalysis\sourceannotations.h>

using namespace vc_attributes;

//requires pc to be null
void f([Pre(Null=Yes)] char* pc);

// calls free and sets ch to null
void FreeAndNull(char** ch);

void test()
{
    char pc = (char)malloc(5);
    FreeAndNull(&pc);
    _Analysis_assume(pc == NULL);
    f(pc);
}
```

## <a name="see-also"></a>另請參閱

- [__assume](../intrinsics/assume.md)
