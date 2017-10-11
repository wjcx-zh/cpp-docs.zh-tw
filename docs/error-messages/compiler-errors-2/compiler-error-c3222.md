---
title: "編譯器錯誤 C3222 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3222
dev_langs:
- C++
helpviewer_keywords:
- C3222
ms.assetid: 5624bde8-2fd0-4b8b-92ce-5dfbaf91cf93
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: edc882f340e92defeaa2db92d868680f7791e7b9
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3222"></a>編譯器錯誤 C3222
'parameter'：無法對 Managed 或 WinRT 類型或泛型函式的成員函式宣告預設引數  
  
不允許宣告具有預設引數的方法參數。 方法的多載形式是解決這個問題的一種方法。 也就是說，定義不含參數的同名方法，然後在方法主體中初始化變數。  
  
下列範例會產生 C3222：  
  
```  
// C3222_2.cpp  
// compile with: /clr  
public ref class G {  
   void f( int n = 0 );   // C3222  
};  
```  

