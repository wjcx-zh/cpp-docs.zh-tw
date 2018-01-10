---
title: "編譯器警告 （層級 1） C4224 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4224
dev_langs: C++
helpviewer_keywords: C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 618e0b12ed20b13d85a7198781d1bec0fea78456
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4224"></a>編譯器警告 (層級 1) C4224
使用非標準擴充： 型式參數 'identifier' 先前已定義為類型  
  
 先前已使用的識別項當做`typedef`。 這會導致 ANSI 相容性警告 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。  
  
## <a name="example"></a>範例  
  
```  
// C4224.cpp  
// compile with: /Za /W1 /LD  
typedef int I;  
void func ( int I );  // C4224  
```