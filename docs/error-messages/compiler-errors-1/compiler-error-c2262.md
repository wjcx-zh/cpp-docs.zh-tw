---
title: "編譯器錯誤 C2262 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2262
dev_langs:
- C++
helpviewer_keywords:
- C2262
ms.assetid: 727d1c6e-53e8-40e5-b7b8-6a7ac2011727
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 62a32d2a15e36819c8b74f35ef5eae57f1abb50f
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2262"></a>編譯器錯誤 C2262
'attribute_specifiers'：InternalsVisibleTo 宣告不能指定版本、文化特性或處理器架構  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>未正確指定屬性。</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
  
## <a name="example"></a>範例  
 下例會產生 C2262。  
  
```  
// C2262.cpp  
// compile with: /clr /c  
using namespace System::Runtime::CompilerServices;  
[assembly: InternalsVisibleTo("assembly_name, version=1.2.3.7")];   // C2262  
[assembly: InternalsVisibleTo("assembly_name ")];   // OK  
```
