---
title: 編譯器錯誤 C2110 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2110
dev_langs:
- C++
helpviewer_keywords:
- C2110
ms.assetid: 48fd76ed-90d6-4a60-9c7b-f6ce9355b4ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18eafefb4aa7694874c1fbdf994189bbd763826b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171047"
---
# <a name="compiler-error-c2110"></a>編譯器錯誤 C2110
'+': 無法對兩個指標進行相加  
  
 嘗試使用加號 ( `+` ) 運算子將兩個指標值相加。  
  
 下列範例會產生 C2110：  
  
```  
// C2110.cpp  
int main() {  
   int a = 0;  
   int *pa;  
   int *pb;  
   a = pa + pb;   // C2110  
}  
```