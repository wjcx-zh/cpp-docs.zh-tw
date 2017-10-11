---
title: "編譯器錯誤 C2842 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2842
dev_langs:
- C++
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 3998ff0b07ba78228ac51bccac047d8889ccf81b
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2842"></a>編譯器錯誤 C2842
'class'：Managed 或 WinRT 類型不可以定義其自身的 'operator new' 或 'operator delete'  
  
 您可以定義自己 * * 運算子 new 或**運算子 delete**管理原生堆積上的記憶體配置。 不過，參考類別不能定義這些運算子，因為它們只會配置於 Managed 堆積上。  

  
 如需詳細資訊，請參閱[使用者定義的運算子 (C + + /CLI)](../../dotnet/user-defined-operators-cpp-cli.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2842。  
  
```  
// C2842.cpp  
// compile with: /clr /c  
ref class G {  
   void* operator new( size_t nSize );   // C2842  
};  
```  

