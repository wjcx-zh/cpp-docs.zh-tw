---
title: "編譯器警告 C4936 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4936
dev_langs:
- C++
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
caps.latest.revision: 12
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
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 58d702067c186eeeea94768a03836b64577961ca
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-c4936"></a>編譯器警告 C4936
以 /clr 或 /clr:pure 編譯時才支援這個 __declspec  
  
 **/Clr: pure** Visual Studio 2015 中的編譯器選項已被取代。  
  
 A `__declspec` ，但不使用修飾詞`__declspec`修飾詞只適用於以其中一個來編譯時[/clr](../../build/reference/clr-common-language-runtime-compilation.md)選項。  
  
 如需詳細資訊，請參閱[appdomain](../../cpp/appdomain.md)和[程序](../../cpp/process.md)。  
  
 C4936 總是發出錯誤。  您可以停用與 C4936[警告](../../preprocessor/warning.md)pragma。  
  
 下列範例會產生 C4936：  
  
```  
// C4936.cpp  
// compile with: /c  
// #pragma warning (disable : 4936)  
__declspec(process) int i;   // C4936  
__declspec(appdomain) int j;   // C4936  
```
