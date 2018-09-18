---
title: 標點符號 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 438b3f0469d1e8426b1e0ec2a19a63d1ae63c041
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039266"
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