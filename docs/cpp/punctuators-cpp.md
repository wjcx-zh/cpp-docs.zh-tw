---
title: 標點符號（C++）
ms.date: 11/04/2016
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
ms.openlocfilehash: cc4e56cd0dce3ae91183a8675eba96f174c3c31f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160967"
---
# <a name="punctuators-c"></a>標點符號（C++）

在 C++ 中的標點符號對於編譯器具有語法和語意上的含意，但本身並不指定產生值的作業。 不論是單獨或組合，有些標點符號也可以是 C++ 運算子，或對前置處理器具有重大意義。

下列任何字元皆視為標點符號：

```
! % ^ & * ( ) - + = { } | ~
[ ] \ ; ' : " < > ? , . / #
```

標點符號 **[]** 、 **（）** 和 **{}** 必須在[轉譯階段](../preprocessor/phases-of-translation.md)4 之後成對出現。

## <a name="see-also"></a>另請參閱

[語彙慣例](../cpp/lexical-conventions.md)
