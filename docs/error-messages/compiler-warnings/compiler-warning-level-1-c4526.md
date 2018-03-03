---
title: "編譯器警告 （層級 1） C4526 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4526
dev_langs:
- C++
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a74d7d2e2c745a4c8e29736c1e3a7fc38892d5f6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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