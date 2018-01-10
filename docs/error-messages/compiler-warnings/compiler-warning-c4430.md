---
title: "編譯器警告 C4430 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4430
dev_langs: C++
helpviewer_keywords: C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 36bf5954387f37ed9527051f900c54ff93da1c6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4430"></a>編譯器警告 C4430
遺漏類型規範 - 假設為 int。 注意： C + + 不支援 default-int  
  
 針對 Visual c + + 2005年所進行的編譯器一致性工作可能會導致這個錯誤： 所有宣告必須明確都指定型別。不會再假設為 int。  
  
 C4430 永遠視為錯誤。  您可以關閉包含此警告`#pragma warning`或**/wd**; 請參閱[警告](../../preprocessor/warning.md)或[/w、 /W0、 /W1、 /W2、 /W3、 /W4、 /w1、 /w2、 /w3、 /w4、 /Wall、 /wd，/ /wo，我們 /Wv，/WX （警告等級）](../../build/reference/compiler-option-warning-level.md)如需詳細資訊。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4430。  
  
```  
// C4430.cpp  
// compile with: /c  
struct CMyClass {  
   CUndeclared m_myClass;  // C4430  
   int m_myClass;  // OK  
};  
  
typedef struct {  
   POINT();   // C4430  
   // try the following line instead  
   // int POINT();  
   unsigned x;  
   unsigned y;  
} POINT;  
```