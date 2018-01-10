---
title: "編譯器警告 （層級 1） C4399 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4399
dev_langs: C++
helpviewer_keywords: C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eff01c29d423b0823b41bf63702cf42ee839a523
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4399"></a>編譯器警告 (層級 1) C4399
'symbol': __declspec （dllimport） 以 /clr 編譯時不會標示每個處理序專屬符號： pure  
  
 **/Clr: pure** Visual Studio 2015 中的編譯器選項已被取代。  
  
 原生映像或原生和 CLR 建構的映像中的資料不會匯純映像。 若要解決這個警告，以編譯**/clr** (不**/clr: pure**) 或刪除`__declspec(dllimport)`。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4399。  
  
```  
// C4399.cpp  
// compile with: /clr:pure /doc /W1 /c  
__declspec(dllimport) __declspec(process) extern const int i;   // C4399  
```