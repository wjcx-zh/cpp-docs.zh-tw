---
title: "編譯器警告 （層級 1） C4662 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4662
dev_langs:
- C++
helpviewer_keywords:
- C4662
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
caps.latest.revision: 5
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: a0cb509f89b6216d7fa8bda21f1b431de0cf6d41
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4662"></a>編譯器警告 (層級 1) C4662
明確具現化 (Explicit Instantiation)；樣板類別 'identifier1' 沒有特製化 'identifier2' 用的定義  
  
 指定的樣板類別已宣告，但未定義。  
  
## <a name="example"></a>範例  
  
```  
// C4662.cpp  
// compile with: /W1 /LD  
template<class T, int i> class MyClass; // no definition  
template MyClass< int, 1>;              // C4662  
```
