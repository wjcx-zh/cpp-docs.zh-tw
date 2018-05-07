---
title: 編譯器警告 （層級 3） C4240 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4240
dev_langs:
- C++
helpviewer_keywords:
- C4240
ms.assetid: a2657cdb-18e1-493f-882b-4e10c0bca71d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f0691230454ffd935d67c99f58b857cdc1ce0f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4240"></a>編譯器警告 (層級 3) C4240
使用非標準擴充： 存取 'classname' 現在已經定義為 '存取規範'，之前它定義為 '存取規範'  
  
 在 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，您無法將存取變更為巢狀類別。 在預設的 Microsoft 擴充功能 (/Ze) 中，您可以產生這則警告。  
  
## <a name="example"></a>範例  
  
```  
// C4240.cpp  
// compile with: /W3  
class X  
{  
private:  
   class N;  
public:  
   class N  
   {   // C4240  
   };  
};  
  
int main()  
{  
}  
```