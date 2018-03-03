---
title: "編譯器錯誤 C2383 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2383
dev_langs:
- C++
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7f89545b9428bd5e901c72d895b5c23317646c26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2383"></a>編譯器錯誤 C2383
'*符號*': 預設引數不允許在這個符號  
  
 C + + 編譯器不允許預設引數函式的指標。  
  
 此程式碼在 Visual Studio 2005 之前的版本，Visual c + + 編譯器已接受，但現在會產生錯誤。 適用於所有版本的 Visual c + + 的程式碼，請勿函式指標的引數指派預設值。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2383，並顯示可能的解決方案：  
  
```cpp  
// C2383.cpp  
// compile with: /c   
void (*pf)(int = 0);   // C2383  
void (*pf)(int);   // OK  
```