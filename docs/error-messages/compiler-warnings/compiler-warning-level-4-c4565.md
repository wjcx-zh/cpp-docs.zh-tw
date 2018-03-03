---
title: "編譯器警告 （層級 4） C4565 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4565
dev_langs:
- C++
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b89da26312c68bc76d23fc829a14f17db3d601b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4565"></a>編譯器警告 (層級 4) C4565
'function': 重複定義;__declspec(modifier) 與先前宣告的符號  
  
 已重新定義的符號，或重新宣告和第二個定義或宣告，不同於第一個定義或宣告中，沒有`__declspec`修飾詞 (***修飾詞***)。 這個警告僅供參考。 若要修正這個警告，請刪除其中一個定義。  
  
 下列範例會產生 C4565:  
  
```  
// C4565.cpp  
// compile with: /W4 /LD  
__declspec(noalias) void f();  
void f();   // C4565  
```