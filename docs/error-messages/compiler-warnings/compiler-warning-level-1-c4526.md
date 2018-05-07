---
title: 編譯器警告 （層級 1） C4526 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4526
dev_langs:
- C++
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5a38d629d61e16b038701522d4bb27a4de7391d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4526"></a>編譯器警告 (層級 1) C4526
'function': 靜態成員函式不能覆寫虛擬函式 ' 虛擬 function'override 略過，將會隱藏虛擬函式  
  
 靜態成員函式符合用來覆寫虛擬函式，讓虛擬和靜態的成員函式的準則。  
  
 下列程式碼會產生 C4526:  
  
```  
// C4526.cpp  
// compile with: /W1 /c  
// C4526 expected  
struct myStruct1 {  
   virtual void __stdcall func( int ) = 0;  
};  
  
struct myStruct2: public myStruct1 {  
   static void __stdcall func( int );  
};  
```  
  
 以下是可能的修正：  
  
-   如果函式的目的是要覆寫基底類別虛擬函式，請移除靜態規範。  
  
-   如果函式的目的是要做為靜態成員函式，將它重新命名，而且不會與基底類別虛擬函式發生衝突。