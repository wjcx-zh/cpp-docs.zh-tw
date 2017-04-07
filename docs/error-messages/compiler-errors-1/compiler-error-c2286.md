---
title: "編譯器錯誤 C2286 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2286
dev_langs:
- C++
helpviewer_keywords:
- C2286
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: c745afd370bd444614fc216ab42fda0f584295e7
ms.lasthandoff: 04/01/2017

---
# <a name="compiler-error-c2286"></a>編譯器錯誤 C2286
'identifier' 表示的成員指標已經設定為 '繼承': 忽略宣告  
  
 類別有兩種不同的指標至成員表示法。  
  
 如需詳細資訊，請參閱[繼承關鍵字](../../cpp/inheritance-keywords.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2286：  
  
```  
// C2286.cpp  
// compile with: /c  
class __single_inheritance X;  
class __multiple_inheritance X;   // C2286  
class  __multiple_inheritance Y;   // OK  
```
