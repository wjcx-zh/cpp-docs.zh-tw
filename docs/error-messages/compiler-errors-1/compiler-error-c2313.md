---
title: 編譯器錯誤 C2313 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2313
dev_langs:
- C++
helpviewer_keywords:
- C2313
ms.assetid: f70eb19b-c0a3-4fb2-ade1-3890a589928d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 984e9e5e9163137537c9da2cd8c14bd1271ebeb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169968"
---
# <a name="compiler-error-c2313"></a>編譯器錯誤 C2313
'type1' : 被參考 ('type2') 攔截，行號  
  
 此例外狀況類型有兩個處理常式。 第二個 catch 的類型會參考第一個 catch 的類型。  
  
 下列範例會產生 C2313：  
  
```  
// C2313.cpp  
// compile with: /EHsc  
#include <eh.h>  
class C {};  
int main() {  
    try {  
        throw "ooops!";  
    }  
    catch( C& ) {}  
    catch( C ) {}   // C2313  
}  
```