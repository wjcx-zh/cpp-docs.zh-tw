---
title: 複合陳述式 (區塊)
ms.date: 11/04/2016
f1_keywords:
- '}'
- '{'
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
ms.openlocfilehash: a06a3d9ce887150ba3333e8e9e874ab337f8b4df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221805"
---
# <a name="compound-statements-blocks"></a>複合陳述式 (區塊)

複合陳述式是由零個或多個以大括弧（**{}**）括住的語句所組成。 複合陳述式可以在必須有陳述式的任何位置使用。 複合陳述式通常稱為「區塊」(Block)。

## <a name="syntax"></a>語法

```
{ [ statement-list ] }
```

## <a name="remarks"></a>備註

下列範例會使用複合陳述式作為語句的*語句*部分（如需 **`if`** 語法的詳細資訊，請參閱[if 語句](../cpp/if-else-statement-cpp.md)）：

```cpp
if( Amount > 100 )
{
    cout << "Amount was too large to handle\n";
    Alert();
}
else
{
    Balance -= Amount;
}
```

> [!NOTE]
> 因為宣告是語句，所以宣告可以是*語句清單*中的其中一個語句。 因此，在複合陳述式內宣告，但未明確宣告為靜態的名稱，會具有區域範圍和 (為物件時) 存留期。 請參閱[範圍](../cpp/scope-visual-cpp.md)，以取得有關使用區域範圍來處理名稱的詳細資料。

## <a name="see-also"></a>另請參閱

[C + + 語句總覽](../cpp/overview-of-cpp-statements.md)
