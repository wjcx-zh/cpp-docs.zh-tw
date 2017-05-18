---
title: "編譯器警告 （層級 1） C4036 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4036
dev_langs:
- C++
helpviewer_keywords:
- C4036
ms.assetid: f0b15359-4d62-48ec-8cb1-a7b36587a47f
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 30ff24d9d8746d914ba4dd098e715d8b5ecb55c9
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4036"></a>編譯器警告 (層級 1) C4036
未命名的 'type' 當做實質參數  
  
 未針對結構、等位、列舉或作為實質參數的類別提供任何類型名稱。 如果您使用[/Zg](../../build/reference/zg-generate-function-prototypes.md)產生函式原型，編譯器會發出這個警告並註解產生的原型中的型式參數。  
  
 請指定類型名稱來解決這個警告。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4036：  
  
```  
// C4036.c  
// compile with: /Zg /W1  
// D9035 expected  
typedef struct { int i; } T;  
void f(T* t) {}   // C4036  
  
// OK  
typedef struct MyStruct { int i; } T2;  
void f2(T2 * t) {}  
```
