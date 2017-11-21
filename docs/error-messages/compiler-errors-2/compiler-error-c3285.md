---
title: "編譯器錯誤 C3285 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3285
dev_langs: C++
helpviewer_keywords: C3285
ms.assetid: 04e8f210-d67e-4810-b153-e1efe2986c8f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a517ec1b163f3092b8dd161bee6cb348ab0129c1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3285"></a>編譯器錯誤 C3285
不能在類型 'type' 的變數上使用 for each 陳述式  
  
 `for each` 陳述式會為陣列或物件集合中的每個項目，重複一組內嵌陳述式。  
  
 如需詳細資訊，請參閱 [for each, in](../../dotnet/for-each-in.md) 。  
  
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