---
title: 編譯器錯誤 C2434 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2434
dev_langs:
- C++
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 543884392698a7a713dbc4c0bfd10dd19fcb0b1c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2434"></a>編譯器錯誤 C2434
'symbol': 以 __declspec （process） 宣告的符號無法以動態方式初始化在 /clr: pure 模式  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
 不可能以動態方式初始化處理序專屬變數下的 **/clr: pure**。 如需詳細資訊，請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)和[程序](../../cpp/process.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2434。  
  
```  
// C2434.cpp  
// compile with: /clr:pure /c  
int f() { return 0; }  
__declspec(process) int i = f();   // C2434  
__declspec(process) int i2 = 0;   // OK  
```