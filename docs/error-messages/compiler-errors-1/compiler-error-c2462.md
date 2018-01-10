---
title: "編譯器錯誤 C2462 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2462
dev_langs: C++
helpviewer_keywords: C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af4b7e303a67ed1eae3d217964818d1b4cd05b96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2462"></a>編譯器錯誤 C2462
'identifier': 無法在 'new-expression' 中定義的型別  
  
 您無法將類型定義的運算元欄位`new`運算子。 將型別定義放在個別的陳述式。  
  
 下列範例會產生 C2462:  
  
```  
// C2462.cpp  
int main() {  
   new struct S { int i; };   // C2462  
}  
```