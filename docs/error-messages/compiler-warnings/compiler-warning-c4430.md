---
title: 編譯器警告 C4430 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4430
dev_langs:
- C++
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 311c75ed1fcacdf8b40f096a759d669c9331c2ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272109"
---
# <a name="compiler-warning-c4430"></a>編譯器警告 C4430
遺漏類型規範 - 假設為 int。 注意： C + + 不支援 default-int  
  
 針對 Visual c + + 2005年所進行的編譯器一致性工作可能會導致這個錯誤： 所有宣告必須明確都指定型別。不會再假設為 int。  
  
 C4430 永遠視為錯誤。  您可以關閉包含此警告`#pragma warning`或 **/wd**; 請參閱[警告](../../preprocessor/warning.md)或[/w、 /W0、 /W1、 /W2、 /W3、 /W4、 /w1、 /w2、 /w3、 /w4、 /Wall、 /wd，/ /wo，我們 /Wv，/WX （警告等級）](../../build/reference/compiler-option-warning-level.md)如需詳細資訊。  
  
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