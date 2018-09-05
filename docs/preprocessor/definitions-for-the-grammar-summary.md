---
title: 文法摘要的定義 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c11f2f839ef806d74eae65c9fc8fe3a71cd2e9c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760808"
---
# <a name="definitions-for-the-grammar-summary"></a>文法摘要的定義

終端是語法定義的端點。 沒有其他解決方式。 終端包括一組保留字和使用者定義的識別項。

非終端在語法中是預留位置。 大部分是在此語法摘要中的其他位置定義。 定義可以是遞迴式。 中定義了下列非終端[語彙慣例](../cpp/lexical-conventions.md)一節*c + + 語言參考*:

`constant`*常數運算式*，*識別項*，*關鍵字*， `operator`， `punctuator`

指出選用元件的註標<sub>opt</sub>。 例如，以下表示以大括號括住的選擇性運算式：

**{** *運算式*<sub>opt</sub> **}**

## <a name="see-also"></a>另請參閱

[文法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)