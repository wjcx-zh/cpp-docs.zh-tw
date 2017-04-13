---
title: "編譯器錯誤 C3087 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3087
dev_langs:
- C++
helpviewer_keywords:
- C3087
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
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
ms.openlocfilehash: f0f26938ae82e2d14ef9d6ca6cf944a4e396c32f
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3087"></a>編譯器錯誤 C3087
'named_argument: 'attribute' 的呼叫已將此成員初始化  
  
 具名引數指定在與相同值之未命名引數的相同屬性區塊中。 請只指定具名或未命名的引數。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3087：  
  
```  
// C3087.cpp  
// compile with: /c  
[idl_quote("quote1", text="quote2")];   // C3087  
[idl_quote(text="quote3")];   // OK  
[idl_quote("quote4")];   // OK  
```
