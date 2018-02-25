---
title: "文法摘要的定義 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 755533d59b9b893da4a657db6da2ea80f13138b5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="definitions-for-the-grammar-summary"></a>文法摘要的定義
終端是語法定義的端點。 沒有其他解決方式。 終端包括一組保留字和使用者定義的識別項。  
  
非終端在語法中是預留位置。 大部分是在此語法摘要中的其他位置定義。 定義可以是遞迴式。 下列非終端項定義於[語彙慣例](../cpp/lexical-conventions.md)區段*c + + 語言參考*:  
  
`constant`*常數運算式*，*識別碼*，*關鍵字*， `operator`， `punctuator`  
  
選擇性的元件會以下標的 opt 表示。 例如，以下表示以大括號括住的選擇性運算式：  
  
**{** *expression*opt **}**  
  
## <a name="see-also"></a>請參閱  
[文法摘要 (C/C++)](../preprocessor/grammar-summary-c-cpp.md)