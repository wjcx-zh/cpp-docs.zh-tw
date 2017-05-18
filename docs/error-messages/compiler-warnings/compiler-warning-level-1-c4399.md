---
title: "編譯器警告 （層級 1） c4399: |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4399
dev_langs:
- C++
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
caps.latest.revision: 9
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 7d7584e318a42530a2a91fee4b428c92bfaf120c
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4399"></a>編譯器警告 (層級 1) C4399
'symbol': __declspec （dllimport） 使用 /clr 編譯時不會標示每個處理序的符號︰ pure  
  
 **/Clr: pure** Visual Studio 2015 中的編譯器選項已被取代。  
  
 原生映像或原生和 CLR 建構與映像中的資料不匯入到純虛擬映像。 若要解決這個警告，以編譯**/clr** (不**/clr: pure**) 或刪除`__declspec(dllimport)`。  
  
## <a name="example"></a>範例  
 下列範例會產生 c4399:。  
  
```  
// C4399.cpp  
// compile with: /clr:pure /doc /W1 /c  
__declspec(dllimport) __declspec(process) extern const int i;   // C4399  
```
