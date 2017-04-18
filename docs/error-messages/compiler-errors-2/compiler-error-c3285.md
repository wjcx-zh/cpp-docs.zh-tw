---
title: "編譯器錯誤 C3285 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3285
dev_langs:
- C++
helpviewer_keywords:
- C3285
ms.assetid: 04e8f210-d67e-4810-b153-e1efe2986c8f
caps.latest.revision: 6
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
ms.openlocfilehash: 5fde3d0a9ec1126ec7c078ccd76c309a2184ecf9
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3285"></a>編譯器錯誤 C3285
不能在類型 'type' 的變數上使用 for each 陳述式  
  
 `for each` 陳述式會為陣列或物件集合中的每個項目，重複一組內嵌陳述式。  
  
 請參閱[針對每個，在](../../dotnet/for-each-in.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3285。  
  
```  
// C3285.cpp  
// compile with: /clr  
int main() {  
   for each (int i in 0) {}   // C3285   
  
   array<int> ^p = { 1, 2, 3 };  
   for each (int j in p) {}   // OK  
}  
```
