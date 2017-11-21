---
title: "編譯器錯誤 C2959 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2959
dev_langs: C++
helpviewer_keywords: C2959
ms.assetid: d66bb2a8-70c3-4209-a358-b0c47f111a50
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 45f0625bd8f7352d6311fad507b1ee5e71a4da1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2959"></a>編譯器錯誤 C2959
泛型類別或函式可能不是樣板的成員  
  
 如需詳細資訊，請參閱[Windows 執行階段和 Managed 樣板](../../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md)和[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2959。  
  
```  
// C2959.cpp  
// compile with: /clr /c  
template <class T> ref struct S {  
   generic <class U> ref struct GR1;   // C2959  
};  
```