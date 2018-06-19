---
title: 編譯器錯誤 C2572 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2572
dev_langs:
- C++
helpviewer_keywords:
- C2572
ms.assetid: f1a42d69-727d-4ce5-88c8-d5f55dea66ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f2211137361d9de86397c333e51abf0a903ff67
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227430"
---
# <a name="compiler-error-c2572"></a>編譯器錯誤 C2572
'member': 重複定義的預設參數： 參數 param  
  
 預設參數不能重新定義。 如果您需要另一個值給參數的預設參數應該未定義。  
  
 下列範例會產生 C2572:  
  
```  
// C2572.cpp  
// compile with: /c  
void f(int i = 1);   // function declaration  
  
// function definition  
void f(int i = 1) {}   // C2572  
  
// try the following line instead  
// void f(int i) {}  
```