---
title: 編譯器錯誤 C2467 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2467
dev_langs:
- C++
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ed9b1b50c63852ed830c2072d7cd8fce668a671
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225639"
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