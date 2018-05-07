---
title: 編譯器錯誤 C2601 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2601
dev_langs:
- C++
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49598223c3f68271065cc6212da19767020c51e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2601"></a>編譯器錯誤 C2601
'function': 區域函式定義不合法  
  
 程式碼會嘗試在函式的函式定義。  
  
 或者，您之前 C2601 錯誤位置的原始程式碼中可能有額外的括號。  
  
 下列範例會產生 C2601:  
  
```  
// C2601.cpp  
int main() {  
   int i = 0;  
  
   void funcname(int j) {   // C2601  
      j++;  
   }  
}  
```