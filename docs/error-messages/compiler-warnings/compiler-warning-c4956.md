---
title: "編譯器警告 C4956 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4956
dev_langs:
- C++
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
caps.latest.revision: 9
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 782735be55c043482679740afa9571ba7b29dfc4
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-c4956"></a>編譯器警告 C4956
'type': 這個類型無法驗證  
  
 會產生這個警告時[/clr: safe](../../build/reference/clr-common-language-runtime-compilation.md)指定且您的程式碼包含不是可驗證的類型。  
  
 如需詳細資訊，請參閱[純粹的和可驗證程式碼 (C + + /CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 這個警告就會發出為錯誤，而且可以停用與[警告](../../preprocessor/warning.md)pragma 或[/wd](../../build/reference/compiler-option-warning-level.md)編譯器選項。  
  
 下列範例會產生 C4956：  
  
```  
// C4956.cpp  
// compile with: /clr:safe  
int* p;   // C4956  
```
