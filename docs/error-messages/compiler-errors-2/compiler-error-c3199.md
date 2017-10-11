---
title: "編譯器錯誤 C3199 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3199
dev_langs:
- C++
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 37443adbfdf65caba83656ca70ff799834fb4eac
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3199"></a>編譯器錯誤 C3199
無效的浮點 pragma 使用方式： 非精確模式不支援例外狀況  
  
 [Float_control](../../preprocessor/float-control.md) pragma 用來指定浮點例外狀況模型[/fp](../../build/reference/fp-specify-floating-point-behavior.md)以外設定**/fp： 精確**。  
  
 下列範例會產生 C3199:  
  
```  
// C3199.cpp  
// compile with: /fp:fast  
#pragma float_control(except, on)   // C3199  
```
