---
title: 編譯器警告 （層級 4） C4032 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4032
dev_langs:
- C++
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb61588c12378972194305d979ecdd89140ac6f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4032"></a>編譯器警告 （層級 4） C4032
型式參數 'number' 有不同的類型，當升級  
  
 參數型別不相容，透過預設升級後，與上一個宣告中的類型。  
  
 這是 ANSI C 中的錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 是 Microsoft 擴充功能 (/Ze) 下的警告。  
  
## <a name="example"></a>範例  
  
```  
// C4032.c  
// compile with: /W4  
void func();  
void func(char);   // C4032, char promotes to int  
  
int main()  
{  
}  
```