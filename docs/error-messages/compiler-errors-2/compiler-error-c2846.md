---
title: 編譯器錯誤 C2846 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2846
dev_langs:
- C++
helpviewer_keywords:
- C2846
ms.assetid: bc090ec2-5410-4112-9ec6-261325374375
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b217e37cf1eb9ed94f6b0a1e2a3ec01d82731f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33242659"
---
# <a name="compiler-error-c2846"></a>編譯器錯誤 C2846
'constructor': 介面不可以有建構函式  
  
 Visual c + +[介面](../../cpp/interface.md)不能有一個建構函式。  
  
 下列範例會產生 C2846:  
  
```  
// C2846.cpp  
// compile with: /c  
__interface C {  
   C();   // C2846 constructor not allowed in an interface  
};  
```