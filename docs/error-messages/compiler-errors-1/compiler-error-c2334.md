---
title: 編譯器錯誤 C2334 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2334
dev_langs:
- C++
helpviewer_keywords:
- C2334
ms.assetid: 36142855-e00b-4bbf-80f5-a301edeff46e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff086a9074db3fca2c85427365b4b90d99b17d24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2334"></a>編譯器錯誤 C2334
未預期的語彙基元，上述 ': 或 {'; 略過函式主體  
  
 下列範例會產生 C2334。 錯誤 C2059 之後，就會發生此錯誤：  
  
```  
// C2334.cpp  
// compile with: /c  
// C2059 expected  
struct s1 {  
   s1   {}   // C2334  
   s1() {}   // OK  
};  
```