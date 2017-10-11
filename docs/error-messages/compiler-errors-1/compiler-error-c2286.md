---
title: "編譯器錯誤 C2286 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
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
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: e1fca7ee629c35c083f6852a914e2ab62b4d5590
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

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
