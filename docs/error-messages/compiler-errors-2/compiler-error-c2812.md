---
title: "編譯器錯誤 C2812 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2812
dev_langs:
- C++
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 12ab4a753ad2098dfa4c3bccb2190c18bcc2fafb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2812"></a>編譯器錯誤 C2812
\#匯入不支援以 /clr: pure 和 /clr: safe  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
 [#import 指示詞](../../preprocessor/hash-import-directive-cpp.md)不支援**/clr: pure**和**/clr: safe**因為`#import`需要原生編譯器支援程式庫使用。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2812。  
  
```  
// C2812.cpp  
// compile with: /clr:pure /c  
#import "importlib.tlb"   // C2812  
```