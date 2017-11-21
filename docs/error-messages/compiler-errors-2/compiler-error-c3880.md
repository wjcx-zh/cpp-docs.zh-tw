---
title: "編譯器錯誤 C3880 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3880
dev_langs: C++
helpviewer_keywords: C3880
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5e86108e0ab2608f7f59f160d9f7a849b83ef71a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3880"></a>編譯器錯誤 C3880
'var': 不可以是常值資料成員  
  
 型別[常值](../../windows/literal-cpp-component-extensions.md)必須是屬性，或編譯時期轉換成下列類型之一：  
  
-   整數類資料類型  
  
-   string  
  
-   具有整數類型或基本類型列舉  
  
 下列範例會產生 C3880:  
  
```  
// C3880.cpp  
// compile with: /clr /c  
ref struct Y1 {  
   literal System::Decimal staticConst1 = 10;   // C3880  
   literal int staticConst2 = 10;   // OK  
};  
```