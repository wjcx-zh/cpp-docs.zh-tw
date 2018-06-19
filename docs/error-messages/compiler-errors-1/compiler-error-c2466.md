---
title: 編譯器錯誤 C2466 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2466
dev_langs:
- C++
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e55e5c130b0a0454577a7155b704a18933b86198
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33224304"
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