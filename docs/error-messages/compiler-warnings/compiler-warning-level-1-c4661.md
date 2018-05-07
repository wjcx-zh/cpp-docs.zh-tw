---
title: 編譯器警告 （層級 1） C4661 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4661
dev_langs:
- C++
helpviewer_keywords:
- C4661
ms.assetid: 603bb8b7-356d-4eef-924b-64d769bac5bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce88913a29dd9ec3f9d5d2e78c3e52ad3ead54fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4661"></a>編譯器警告 (層級 1) C4661
'identifier': 未提供明確樣板具現化要求的合適定義  
  
 未定義樣板類別的成員。  
  
## <a name="example"></a>範例  
  
```  
// C4661.cpp  
// compile with: /W1 /LD  
template<class T> class MyClass {  
public:  
   void i();   // declaration but not definition  
};  
template MyClass< int >;  // C4661  
```