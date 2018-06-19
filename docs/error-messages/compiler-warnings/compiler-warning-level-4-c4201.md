---
title: 編譯器警告 （層級 4） C4201 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4201
dev_langs:
- C++
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56805506c112d0d92b627b905199bcbbeae8d2f7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292288"
---
# <a name="compiler-warning-level-4-c4201"></a>編譯器警告 (層級 4) C4201
使用非標準擴充： 沒有名稱的結構/等位  
  
 Microsoft 擴充功能 (/Ze) 下您可以指定沒有宣告子結構做為另一個結構或等位的成員。 這些結構產生 ANSI 相容性錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。  
  
## <a name="example"></a>範例  
  
```  
// C4201.cpp  
// compile with: /W4  
struct S  
{  
   float y;  
   struct  
   {  
      int a, b, c;  // C4201  
   };  
} *p_s;  
  
int main()  
{  
}  
```