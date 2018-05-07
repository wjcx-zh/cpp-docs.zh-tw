---
title: 編譯器警告 （層級 4） C4516 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4516
dev_langs:
- C++
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5ca56734d5bd9f2ddf66732ed894d805e368664
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4516"></a>編譯器警告 (層級 4) C4516
'class::symbol': 已被取代存取宣告;成員 using 宣告提供較佳替代方式  
  
 ANSI c + + committee 已宣告存取宣告 (變更而不在衍生類別中成員的存取權[使用](../../cpp/using-declaration.md)關鍵字) 為過期。 C + + 的未來版本可能不支援存取宣告。  
  
 下列範例會產生 C4516:  
  
```  
// C4516.cpp  
// compile with: /W4  
class A  
{  
public:  
   void x(char);  
};  
  
class B : protected A  
{  
public:  
   A::x;  // C4516 on access-declaration  
   // use the following line instead  
   // using A::x; // using-declaration, ok  
};  
  
int main()  
{  
}  
```