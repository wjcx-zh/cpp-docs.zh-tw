---
title: "編譯器錯誤 C2531 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2531
dev_langs: C++
helpviewer_keywords: C2531
ms.assetid: c49afe15-55f8-4dc8-ac01-bf653622a7db
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5696fdd631f23f2ac53d5e9677085d8709817e38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2531"></a>編譯器錯誤 C2531
'identifier': 位元欄位不合法的參考  
  
 不允許位元欄位的參考。  
  
 下列範例會產生 C2531:  
  
```  
// C2531.cpp  
// compile with: /c  
class P {  
   int &b1 : 10;   // C2531  
   int b2 : 10;   // OK  
};  
```