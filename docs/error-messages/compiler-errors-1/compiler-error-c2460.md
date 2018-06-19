---
title: 編譯器錯誤 C2460 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2460
dev_langs:
- C++
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4220be654f93ecd79d196efc14657ca7346411f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197776"
---
# <a name="compiler-error-c2460"></a>編譯器錯誤 C2460
'identifier1': 使用 'identifier2'，已經定義的  
  
 類別或結構 (`identifier2`) 宣告為本身的成員 (`identifier1`)。 不允許遞迴定義的類別和結構。  
  
 下列範例會產生 C2460:  
  
```  
// C2460.cpp  
class C {  
   C aC;    // C2460  
};  
```  
  
 相反地，在類別中使用指標參考。  
  
```  
// C2460.cpp  
class C {  
   C * aC;    // OK  
};  
```