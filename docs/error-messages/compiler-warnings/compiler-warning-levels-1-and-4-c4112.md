---
title: "編譯器警告 （層級 1 和 4） C4112 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4112
dev_langs:
- C++
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 8a2c08b6c4bc8e1f2cf20e0236f76b5cd3020de4
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>編譯器警告 (層級 1 和 4) C4112
\#行需要 1 與數字之間的整數  
  
 [#Line](../../preprocessor/hash-line-directive-c-cpp.md)指示詞會指定超出容許範圍的整數參數。  
  
 如果指定的參數小於 1，行計數器就會重設為 1。 如果指定的參數大於編譯器定義限制的 *數字*，行計數器不會變更。 這是 ANSI 相容性層級 1 警告 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 和具有 Microsoft 擴充功能的層級 4 警告 ([/Ze](../../build/reference/za-ze-disable-language-extensions.md))。  
  
 下列範例會產生 C4112：  
  
```  
// C4112.cpp  
// compile with: /W4  
#line 0   // C4112, value must be between 1 and number  
  
int main() {  
}  
```
