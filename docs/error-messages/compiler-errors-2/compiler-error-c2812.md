---
title: "編譯器錯誤 C2812 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2812
dev_langs:
- C++
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
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
ms.openlocfilehash: 358d0d3a5c7f0129d74be70c3309337542807d1d
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2812"></a>編譯器錯誤 C2812
\#匯入不支援使用 /clr: pure 和 /clr: safe  
  
 **/Clr: pure**和**/clr: safe** Visual Studio 2015 中的編譯器選項已被取代。  
  
 [#import 指示詞](../../preprocessor/hash-import-directive-cpp.md)不支援**/clr: pure**和**/clr: safe**因為`#import`需要使用原生編譯器支援程式庫。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2812。  
  
```  
// C2812.cpp  
// compile with: /clr:pure /c  
#import "importlib.tlb"   // C2812  
```
