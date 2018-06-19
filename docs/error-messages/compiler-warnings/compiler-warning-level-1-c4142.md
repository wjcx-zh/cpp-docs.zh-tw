---
title: 編譯器警告 （層級 1） C4142 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4142
dev_langs:
- C++
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c87b7689cf11ab28c1a6377ff85e1594fd1b5fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284429"
---
# <a name="compiler-warning-level-1-c4142"></a>編譯器警告 （層級 1） C4142
良性的類型重複定義  
  
 類型已重新定義不有任何影響產生的程式碼的方式。  
  
 您可以檢查下列可能的原因來進行修正：  
  
-   在衍生類別的成員函式具有不同傳回的型別對應的成員函式的基底類別。  
  
-   與定義的型別`typedef`命令已重新定義，使用不同的語法。  
  
 下列範例會產生 C4142:  
  
```  
// C4142.c  
// compile with: /W1  
float X2;  
X2 = 2.0 + 1.0;   // C4142  
  
int main() {  
   float X2;  
   X2 = 2.0 + 1.0;   // OK  
}  
```