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
ms.openlocfilehash: 0ac3b742406f1e8be955921a9ee238f3b35d3bdf
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "42545754"
---
# <a name="definitions-for-the-grammar-summary"></a>文法摘要的定義
終端是語法定義的端點。 沒有其他解決方式。 終端包括一組保留字和使用者定義的識別項。  
  
非終端在語法中是預留位置。 大部分是在此語法摘要中的其他位置定義。 定義可以是遞迴式。 中定義了下列非終端[語彙慣例](../cpp/lexical-conventions.md)一節*c + + 語言參考*:  
  
`constant`*常數運算式*，*識別項*，*關鍵字*， `operator`， `punctuator`  
  
選擇性的元件會以下標的 opt 表示。 例如，以下表示以大括號括住的選擇性運算式：  
  
**{** *運算式*opt **}**  
  
## <a name="see-also"></a>另請參閱 
 
[文法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)