---
title: "編譯器錯誤 C2466 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2466
dev_langs:
- C++
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a41ea550abff9e48973452996cf5621e6bc4c42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2466"></a>編譯器錯誤 C2466
無法配置常數大小為 0 的陣列  
  
 配置陣列，或宣告大小為零。 陣列大小的常數運算式必須是大於零的整數。 陣列宣告使用零註標是合法的只有類別、 結構或等位成員，只能搭配 Microsoft 擴充功能 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。  
  
 下列範例會產生 C2466:  
  
```  
// C2466.cpp  
// compile with: /c  
int i[0];   // C2466  
int j[1];   // OK  
char *p;  
```