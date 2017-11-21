---
title: "編譯器錯誤 C2710 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2710
dev_langs: C++
helpviewer_keywords: C2710
ms.assetid: a2a6bb5b-86ad-4a6c-acd0-e2bef8464e0e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5bb6349bf6efb8c63b68c78644343ace5dc07e67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2710"></a>編譯器錯誤 C2710
'construct': '__declspec(modifier)' 只能套用至傳回指標的函式  
  
 傳回值是指標的函式是要唯一建構`modifier`可以套用。  
  
 下列範例會產生 C2710:  
  
```  
// C2710.cpp  
__declspec(restrict) void f();   // C2710  
// try the following line instead  
__declspec(restrict) int * g();  
```