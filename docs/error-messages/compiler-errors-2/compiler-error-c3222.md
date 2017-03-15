---
title: "編譯器錯誤 C3222 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: bd1058f4e33bc70c9021bfb1ceff78af58d09552
ms.lasthandoff: 02/24/2017

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

