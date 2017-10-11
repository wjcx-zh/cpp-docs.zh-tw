---
title: "編譯器錯誤 C2758 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2758
dev_langs:
- C++
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: f694df9f39edbc257b887bcfd9bd13a0ba31a1a0
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2758"></a>編譯器錯誤 C2758
'member'：必須初始化參考類型的成員  
  
 當建構函式未初始化初始設定式清單中參考類型的成員時，會產生編譯器錯誤 C2758。 編譯器會將成員保持未定義的狀態。 在建構函式的初始化清單中宣告參考成員變數或提供值時，必須初始化。  
  
 下列範例會產生 C2758：  
  
```  
// C2758.cpp  
// Compile by using: cl /W3 /c C2758.cpp  
struct A {  
   const int i;  
  
   A(int n) { };   // C2758  
   // try the following line instead  
   // A(int n) : i{n} {};  
};  
```
