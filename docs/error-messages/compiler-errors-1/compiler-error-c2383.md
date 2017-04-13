---
title: "編譯器錯誤 C2383 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2383
dev_langs:
- C++
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: faa2aa2c29ea34009f0812a3796d450a6877ca48
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2383"></a>編譯器錯誤 C2383
'*符號*': 預設引數不允許在這個符號  
  
 C + + 編譯器不允許預設引數函式的指標。  
  
 此程式碼在 Visual Studio 2005 之前的版本，Visual c + + 編譯器已接受，但現在會產生錯誤。 適用於所有版本的 Visual c + + 的程式碼，請勿函式指標的引數指派預設值。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2383，並顯示可能的解決方案︰  
  
```cpp  
// C2383.cpp  
// compile with: /c   
void (*pf)(int = 0);   // C2383  
void (*pf)(int);   // OK  
```
