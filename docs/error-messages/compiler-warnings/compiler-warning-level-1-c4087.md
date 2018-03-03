---
title: "編譯器警告 （層級 1） C4087 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4087
dev_langs:
- C++
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ef21fc01fc6c756eb68f90bd58f9b18456e12fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4087"></a>編譯器警告 (層級 1) C4087
'function' : 搭配 'void' 參數清單宣告  
  
 函式宣告沒有型式參數，但函式呼叫有實際的參數。 根據函式的呼叫慣例，傳遞了額外的參數。  
  
 這項警告是對於 C 編譯器。  
  
## <a name="example"></a>範例  
  
```  
// C4087.c  
// compile with: /W1  
int f1( void ) {  
}  
  
int main() {  
   f1( 10 );   // C4087  
}  
```