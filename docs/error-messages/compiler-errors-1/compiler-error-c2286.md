---
title: 編譯器錯誤 C2286 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2286
dev_langs:
- C++
helpviewer_keywords:
- C2286
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ddfb523252572fb985b660f1d4dbf5b1d790df1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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