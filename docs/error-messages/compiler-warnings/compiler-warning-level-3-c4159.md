---
title: "編譯器警告 （層級 3） C4159 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4159
dev_langs: C++
helpviewer_keywords: C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1997fc9b210723c5747f67e3b042987043c5c161
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4159"></a>編譯器警告 （層級 3） C4159
\#pragma pragma(pop,...)： 已經推出之前推入的識別項 'identifier'  
  
 您的原始程式碼包含**推入**指令的識別項的 pragma 後面**pop**指令沒有識別項。 如此一來，***識別碼***已推出，及後續使用***識別碼***可能會造成非預期的行為。  
  
 若要避免這個警告，提供一個識別項**pop**指令。 例如:   
  
```  
// C4159.cpp  
// compile with: /W3  
#pragma pack(push, f)  
#pragma pack(pop)   // C4159  
  
// using the identifier resolves the warning  
// #pragma pack(pop, f)  
  
int main()  
{  
}  
```