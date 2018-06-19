---
title: 編譯器警告 （層級 4） C4670 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4670
dev_langs:
- C++
helpviewer_keywords:
- C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9bec30fff715984073aa3061979fff11923f0bf8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315356"
---
# <a name="compiler-warning-level-4-c4670"></a>編譯器警告 (層級 4) C4670
'identifier': 此基底類別無法存取  
  
 無法存取要在 **try** 區塊中擲回之物件的指定基底類別。 如果擲回物件，則無法具現化物件。 請檢查使用正確的存取規範來繼承基底類別。  
  
 下列範例會產生 C4670：  
  
```  
// C4670.cpp  
// compile with: /EHsc /W4  
class A  
{  
};  
  
class B : /* public */ A  
{  
} b;   // inherits A with private access by default  
  
int main()  
{  
    try  
    {  
       throw b;   // C4670  
    }  
    catch( B )  
    {  
    }  
}  
```