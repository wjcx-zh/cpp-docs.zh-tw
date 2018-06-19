---
title: 編譯器錯誤 C2790 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2790
dev_langs:
- C++
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11f1c90fed93666fad7513e2b4186a5baa2aa406
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232813"
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