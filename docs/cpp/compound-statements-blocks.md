---
title: 複合陳述式 （區塊） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '}'
- '{'
dev_langs:
- C++
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89e243dd1905e61a6c9a1b16c1936d7d6617ba17
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116811"
---
# <a name="compound-statements-blocks"></a>複合陳述式 (區塊)

複合陳述式包含大括號括住的零或多個陳述式 (**{}**)。 複合陳述式可以在必須有陳述式的任何位置使用。 複合陳述式通常稱為「區塊」(Block)。

## <a name="syntax"></a>語法

```
{ [ statement-list ] }
```

## <a name="remarks"></a>備註

下列範例會使用複合陳述式，作為*陳述式*屬於**如果**陳述式 (請參閱[if 陳述式](../cpp/if-else-statement-cpp.md)如需語法的詳細資訊):

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
>  由於宣告是陳述式，宣告可以是其中一個陳述式中*陳述式清單*。 因此，在複合陳述式內宣告，但未明確宣告為靜態的名稱，會具有區域範圍和 (為物件時) 存留期。 請參閱[範圍](../cpp/scope-visual-cpp.md)具有本機領域的名稱的處理方式的詳細資料。

## <a name="see-also"></a>另請參閱

[C++ 陳述式概觀](../cpp/overview-of-cpp-statements.md)