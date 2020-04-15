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
ms.openlocfilehash: 60d7e88c5ccccac5a1d967a91c8a82dd954d9afc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337335"
---
# <a name="compound-statements-blocks"></a>複合陳述式 (區塊)

複合語句由以大括弧 **(***) 括起來的零個或多個語句組成。 複合陳述式可以在必須有陳述式的任何位置使用。 複合陳述式通常稱為「區塊」(Block)。

## <a name="syntax"></a>語法

```
{ [ statement-list ] }
```

## <a name="remarks"></a>備註

下面的範例使用複合語句作為**if** *語句的語句*部分(有關語法的詳細資訊,請參閱[if 語句](../cpp/if-else-statement-cpp.md)):

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
> 由於聲明是語句,因此聲明可以是*語句清單中*的語句之一。 因此，在複合陳述式內宣告，但未明確宣告為靜態的名稱，會具有區域範圍和 (為物件時) 存留期。 有關使用本地作用域的名稱的處理的詳細資訊,請參閱[Scope。](../cpp/scope-visual-cpp.md)

## <a name="see-also"></a>另請參閱

[C++宣告概述](../cpp/overview-of-cpp-statements.md)
