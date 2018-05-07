---
title: 編譯器警告 （層級 1） C4216 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4216
dev_langs:
- C++
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2de645b2d036e7ed696a8065bbb9f8212ec5c596
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4216"></a>編譯器警告 (層級 1) C4216
使用非標準擴充： float long  
  
 預設的 Microsoft 擴充功能 (/Ze) 視為**float long**為**double**。 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 並不會。 使用**double**維護相容性。 下列範例會產生 C4216:  
  
```  
// C4216.cpp  
// compile with: /W1  
float long a;   // C4216  
  
// use the line below to resolve the warning  
// double a;  
  
int main() {  
}  
```