---
title: 標點符號 （c + +）
ms.date: 11/04/2016
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
ms.openlocfilehash: cef34a17de99a189a590ac3f13c0db9563df643c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478260"
---
# <a name="punctuators-c"></a>標點符號 （c + +）

在 C++ 中的標點符號對於編譯器具有語法和語意上的含意，但本身並不指定產生值的作業。 不論是單獨或組合，有些標點符號也可以是 C++ 運算子，或對前置處理器具有重大意義。

下列任何字元皆視為標點符號：

```
! % ^ & * ( ) - + = { } | ~
[ ] \ ; ' : " < > ? , . / #
```

標點符號 **[]**， **> （)**，並 **{}** 必須出現在配對後[轉譯階段](../preprocessor/phases-of-translation.md)4。

## <a name="see-also"></a>另請參閱

[語彙慣例](../cpp/lexical-conventions.md)