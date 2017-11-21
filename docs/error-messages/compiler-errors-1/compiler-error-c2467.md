---
title: "編譯器錯誤 C2467 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2467
dev_langs: C++
helpviewer_keywords: C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a51321e6597bffe0dded58ffa481f054e770f9b7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2467"></a>編譯器錯誤 C2467
匿名 '使用者定義的型別' 的宣告不合法  
  
 巢狀的使用者定義型別宣告。 這是在編譯 C 原始程式碼，與 ANSI 相容性選項時的錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 啟用。  
  
 下列範例會產生 C2467:  
  
```  
//C2467.c  
// compile with: /Za   
int main() {  
   struct X {  
      union { int i; };   // C2467, nested declaration  
   };  
}  
```