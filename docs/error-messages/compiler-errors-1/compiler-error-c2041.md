---
title: 編譯器錯誤 C2041 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2041
dev_langs:
- C++
helpviewer_keywords:
- C2041
ms.assetid: c9a33bb1-f9cf-47d6-bd21-7d867a8c37d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 747dd5621aec556e89fee2ab8e7ff512736e408c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164462"
---
# <a name="compiler-error-c2041"></a>編譯器錯誤 C2041
不合法的數字的基底 'number' 的 ' character'  
  
 指定的字元不是有效的數字 （例如八進位或十六進位） 基底。  
  
 下列範例會產生 C2041:  
  
```  
// C2041.cpp  
int i = 081;   // C2041  8 is not a base 8 digit  
```  
  
 可能的解決方式：  
  
```  
// C2041b.cpp  
// compile with: /c  
int j = 071;  
```