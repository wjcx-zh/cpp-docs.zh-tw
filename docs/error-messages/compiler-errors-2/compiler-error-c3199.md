---
title: 編譯器錯誤 C3199 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3199
dev_langs:
- C++
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cddad2218e81603f59cad51e3a684303e144171e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3199"></a>編譯器錯誤 C3199
無效的浮點 pragma 使用方式： 非精確模式不支援例外狀況  
  
 [Float_control](../../preprocessor/float-control.md) pragma 用來指定浮點例外狀況模型[/fp](../../build/reference/fp-specify-floating-point-behavior.md)以外設定 **/fp： 精確**。  
  
 下列範例會產生 C3199:  
  
```  
// C3199.cpp  
// compile with: /fp:fast  
#pragma float_control(except, on)   // C3199  
```