---
title: 編譯器錯誤 C2588 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2588
dev_langs:
- C++
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67eb6362ff55e09b05349d10fcdc2377d8ff2996
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231666"
---
# <a name="compiler-error-c2588"></a>編譯器錯誤 C2588
':: ~ 識別項 ': 不合法的全域解構函式  
  
 解構函式定義的項目以外的類別、 結構或等位。 這是不允許的。  
  
 這個錯誤可能因遺失類別、 結構或等位名稱左邊的範圍解析 (`::`) 運算子。  
  
 下列範例會產生 C2588:  
  
```  
// C2588.cpp  
~F();   // C2588  
```