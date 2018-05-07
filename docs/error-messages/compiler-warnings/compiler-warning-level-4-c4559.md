---
title: 編譯器警告 （層級 4） C4559 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4559
dev_langs:
- C++
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c853fa55482604d97c29653fadb06b0afdd44977
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4559"></a>編譯器警告 (層級 4) C4559
'function': 重複定義;此函式取得 __declspec(modifier)  
  
 函式已重新定義或宣告，但第二個定義或宣告加入 __**declspec**修飾詞 (***修飾詞***)。 這個警告僅供參考。 若要修正這個警告，請刪除其中一個定義。  
  
 下列範例會產生 C4559:  
  
```  
// C4559.cpp  
// compile with: /W4 /LD  
void f();  
__declspec(noalias) void f();   // C4559  
```