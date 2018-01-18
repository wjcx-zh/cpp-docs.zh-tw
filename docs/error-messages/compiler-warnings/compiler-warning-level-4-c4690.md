---
title: "編譯器警告 （層級 4） C4690 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4690
dev_langs: C++
helpviewer_keywords: C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e1307a571e38cf7e4ef81f7c9c08a07bf5c833c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4690"></a>編譯器警告 (層級 4) C4690
[ emitidl( pop ) ] : pop 的數目必須和 push 相同，否則可能導致非預期的行為  
  
 [emitidl](../../windows/emitidl.md) 屬性的 pop 作業比 push 作業多一次。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4690。  
  
```  
// C4690.cpp  
// compile with: /c /W4  
[emitidl(pop)];   // C4690  
class x {};  
```