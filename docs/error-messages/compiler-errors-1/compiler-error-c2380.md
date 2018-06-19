---
title: 編譯器錯誤 C2380 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2380
dev_langs:
- C++
helpviewer_keywords:
- C2380
ms.assetid: 717b1e6e-ddfe-4bac-a5f3-7f9a4dcb1572
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa2d0fc361f1cf5ba5355ca11ce86279ebd3575f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33195629"
---
# <a name="compiler-error-c2380"></a>編譯器錯誤 C2380
型別前面 'identifier' （具有建構函式傳回型別或目前的類別名稱的重新定義不合法？）  
  
 建構函式會傳回值，或重新定義的類別名稱。  
  
 下列範例會產生 C2326：  
  
```  
// C2380.cpp  
// compile with: /c  
class C {  
public:  
   int C();   // C2380, specifies an int return  
   int C;   // C2380, redefinition of i  
   C();   // OK  
};  
```