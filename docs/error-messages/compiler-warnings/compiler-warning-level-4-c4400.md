---
title: "編譯器警告 （層級 4） C4400 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4400
dev_langs: C++
helpviewer_keywords: C4400
ms.assetid: f135fe98-4f92-4e07-9d71-2621b36ee755
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 975127c09a44448c5589edfd3b63323caa23f942
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4400"></a>編譯器警告 (層級 4) C4400
'type': 不支援此類型的 const/volatile 限定詞  
  
 [Const](../../cpp/const-cpp.md)和[volatile](../../cpp/volatile-cpp.md)限定詞不適用於 common language runtime 類型的變數。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4400。  
  
```  
// C4400.cpp  
// compile with: /clr /W4  
// C4401 expected  
using namespace System;  
#pragma warning (disable : 4101)  
int main() {  
   const String^ str;   // C4400  
   volatile String^ str2;   // C4400  
}  
```