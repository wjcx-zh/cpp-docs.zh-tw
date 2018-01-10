---
title: "編譯器錯誤 C3612 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3612
dev_langs: C++
helpviewer_keywords: C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b4cb0ecfbff311878137ea0c80f53388900ba7cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3612"></a>編譯器錯誤 C3612
'type': 密封的類別不能為抽象  
  
使用定義的型別`value`會根據預設，密封和類別是抽象的除非它會實作其基底的所有方法。 密封的抽象類別不能是基底類別，也可以它具現化。  
  
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