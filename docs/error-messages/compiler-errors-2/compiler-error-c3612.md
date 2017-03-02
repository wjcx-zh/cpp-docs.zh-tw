---
title: "編譯器錯誤 C3612 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3612
dev_langs:
- C++
helpviewer_keywords:
- C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
caps.latest.revision: 11
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
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: fa36c033cf311538e1d77ce37b2d3e4a3936b7d7
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3612"></a>編譯器錯誤 C3612
'type': 密封的類別不能是抽象  
  
使用定義的型別`value`根據預設，已密封和類別是抽象的除非它會實作其基底的所有方法。 密封的抽象類別都不可以是基底類別，也可以在初始化。  
  
如需詳細資訊，請參閱[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
下列範例會產生 C3612:  
  
```  
// C3612.cpp  
// compile with: /clr /c  
value struct V: public System::ICloneable {};   // C3612  
  
// OK  
value struct V2: public System::ICloneable {  
   Object^ Clone();  
};  
```
