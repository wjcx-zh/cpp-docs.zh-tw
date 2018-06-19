---
title: 編譯器錯誤 C2130 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2130
dev_langs:
- C++
helpviewer_keywords:
- C2130
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4484d183def04f764ae75faaa503449e7bdf9984
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172072"
---
# <a name="compiler-error-c2130"></a>編譯器錯誤 C2130
\#行必須是字串，包含檔名，找到 'token'  
  
 [#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` 後面的選擇性檔名語彙基元必須是字串。  
  
 下列範例會產生 C2130：  
  
```  
// C2130.cpp  
int main() {  
   #line 1000 test   // C2130  
   #line 1000 "test"   // OK  
}  
```