---
title: "編譯器錯誤 C2435 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2435
dev_langs:
- C++
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
caps.latest.revision: 12
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
ms.openlocfilehash: dbc2045eae70cacd42e13ddb7cc8ecb3d60b8596
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2435"></a>編譯器錯誤 C2435
'var': 動態初始化需要受管理的 CRT，無法編譯以 /clr: safe  
  
 **/Clr: pure**和**/clr: safe** Visual Studio 2015 中的編譯器選項已被取代。  
  
 全域 – 應用程式網域變數的初始化需要使用 CRT `/clr:pure`，這不會產生可驗證映像。  
  
 如需詳細資訊，請參閱[appdomain](../../cpp/appdomain.md)和[程序](../../cpp/process.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2435:  
  
```  
// C2435.cpp  
// compile with: /clr:safe /c  
int globalvar = 0;   // C2435  
  
__declspec(process)  
int globalvar2 = 0;  
```
