---
title: 編譯器警告 （層級 2） C4094 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4094
dev_langs:
- C++
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9deae6a0e21fcb7dd4f09de07e65445dc9595932
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-2-c4094"></a>編譯器警告 （層級 2） C4094
未標記 ' token' 宣告沒有符號  
  
 編譯器偵測到空的宣告使用標記的結構、 等位或類別。 宣告會被忽略。  
  
## <a name="example"></a>範例  
  
```  
// C4094.cpp  
// compile with: /W2  
struct  
{  
};   // C4094  
  
int main()  
{  
}  
```  
  
 這種情況會產生 ANSI 相容性錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。