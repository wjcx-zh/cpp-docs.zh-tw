---
title: "編譯器錯誤 C2790 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2790
dev_langs:
- C++
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 11ea7285d20808f16f2588d50caebe99429c8da0
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2790"></a>編譯器錯誤 C2790
'super': 此關鍵字只用於類別成員函式主體內  
  
 如果使用者曾嘗試使用關鍵字出現下列錯誤訊息[super](../../cpp/super.md)成員函式的環境之外。  
  
 下列範例會產生 C2790:  
  
```  
// C2790.cpp  
void f() {  
   __super::g();   // C2790  
}  
```
