---
title: "編譯器錯誤 C2434 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2434
dev_langs:
- C++
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
caps.latest.revision: 6
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
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 65aac590a3282f2fd71c460d14927f5695fcdc5a
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2434"></a>編譯器錯誤 C2434
'symbol': __declspec(process) 以宣告的符號不動態初始化在 /clr: pure 模式  
  
 **/Clr: pure**和**/clr: safe** Visual Studio 2015 中的編譯器選項已被取代。  
  
 不可能以動態方式來初始化每個處理序變數下的**/clr: pure**。 如需詳細資訊，請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)和[程序](../../cpp/process.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 c2434:。  
  
```  
// C2434.cpp  
// compile with: /clr:pure /c  
int f() { return 0; }  
__declspec(process) int i = f();   // C2434  
__declspec(process) int i2 = 0;   // OK  
```
