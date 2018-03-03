---
title: "編譯器警告 （層級 4） C4559 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4559
dev_langs:
- C++
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa3dcd3bc2af9e7a9376ff6a2e5db31dbbe9c898
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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