---
title: "編譯器警告 （層級 1） C4661 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4661
dev_langs: C++
helpviewer_keywords: C4661
ms.assetid: 603bb8b7-356d-4eef-924b-64d769bac5bd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 369644c97430abe3d0f2c263a61aa3ce27663ed6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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