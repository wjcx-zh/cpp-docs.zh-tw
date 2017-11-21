---
title: "編譯器警告 （層級 1） C4286 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4286
dev_langs: C++
helpviewer_keywords: C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 71abc86a66f08cbdceb422b74fa5ca600b110a0f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4286"></a>編譯器警告 (層級 1) C4286
'type1': 捕捉到的行號的基底類別 ('type2')  
  
 指定的例外狀況類型是由前一個處理常式處理。 第二個 catch 的類型被衍生自第一個型別。 基底類別的例外狀況攔截例外狀況衍生的類別。  
  
## <a name="example"></a>範例  
  
```  
//C4286.cpp  
// compile with: /W1  
#include <eh.h>  
class C {};  
class D : public  C {};  
int main()  
{  
    try  
    {  
        throw "ooops!";  
    }  
    catch( C ) {}  
    catch( D ) {}  // warning C4286, D is derived from C  
}  
```