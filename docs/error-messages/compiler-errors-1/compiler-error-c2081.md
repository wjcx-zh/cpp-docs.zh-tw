---
title: "編譯器錯誤 C2081 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2081
dev_langs:
- C++
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 20f9f98ca03b9ed71d360b1b7c8bb64494a58416
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2081"></a>編譯器錯誤 C2081
'identifier': 型式參數清單不合法的名稱  
  
 識別項會導致語法錯誤。  
  
 這個錯誤可能被因使用舊樣式型式參數清單。 您必須指定型式參數的型別之型式參數清單中。  
  
 下列範例會產生 C2081:  
  
```  
// C2081.c  
void func( int i, j ) {}  // C2081, no type specified for j  
```  
  
 可能的解決方式：  
  
```  
// C2081b.c  
// compile with: /c  
void func( int i, int j ) {}  
```
