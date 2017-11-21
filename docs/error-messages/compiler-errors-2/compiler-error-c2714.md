---
title: "編譯器錯誤 C2714 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2714
dev_langs: C++
helpviewer_keywords: C2714
ms.assetid: 401a5a42-660c-4bad-9d63-1a2d092bc489
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1f0fc4847cc6f3ab50f840b1ed5a097cc405cff8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2714"></a>編譯器錯誤 C2714
不允許 __alignof(void)  
  
 無效的值傳遞給操作員。  
  
 請參閱[__alignof 運算子](../../cpp/alignof-operator.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2714。  
  
```  
// C2714.cpp  
int main() {  
   return __alignof(void);   // C2714  
   return __alignof(char);   // OK  
}  
```