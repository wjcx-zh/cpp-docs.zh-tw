---
title: 編譯器錯誤 C3880 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3880
dev_langs:
- C++
helpviewer_keywords:
- C3880
ms.assetid: b0e05d1e-32d0-4034-9246-f37d23573ea9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34cc36f3b5fb9571a707e4ffe4e75182e984e407
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269753"
---
# <a name="compiler-error-c3880"></a>編譯器錯誤 C3880
'var': 不可以是常值資料成員  
  
 型別[常值](../../windows/literal-cpp-component-extensions.md)必須是屬性，或編譯時期轉換成下列類型之一：  
  
-   整數類資料類型  
  
-   字串  
  
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