---
title: 文法摘要的定義
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
ms.openlocfilehash: 93cf6ffc5daf53a106c9f15a2289e2b52739d72f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222419"
---
# <a name="definitions-for-the-grammar-summary"></a>文法摘要的定義

終端是語法定義的端點。 沒有其他解決方式。 終端包括一組保留字和使用者定義的識別項。

非終端在語法中是預留位置。 大部分是在此語法摘要中的其他位置定義。 定義可以是遞迴式。 下列非終端項定義于 *C++語言參考*的 [[詞彙慣例](../cpp/lexical-conventions.md)] 區段中:

*常數*、*常數運算式*、*識別碼*、*關鍵字*、*運算子*、*標點符號*

選擇性的元件會以下標的 <sub>opt</sub> 表示。 例如，以下表示以大括號括住的選擇性運算式：

**{** *運算式*<sub>opt</sub> **}**

## <a name="see-also"></a>另請參閱

[文法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)
