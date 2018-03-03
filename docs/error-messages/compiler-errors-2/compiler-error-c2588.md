---
title: "編譯器錯誤 C2588 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2588
dev_langs:
- C++
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 807574f0f94f989726ca19d3260b9668f6c84055
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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