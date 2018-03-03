---
title: "編譯器錯誤 C2388 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2388
dev_langs:
- C++
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa9f970d71be7b19551ef5029df49b696eb353e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2388"></a>編譯器錯誤 C2388
'symbol': 符號不可宣告與這兩個 __declspec(appdomain) 和\__declspec(process)  
  
 `appdomain` 和 `process` `__declspec` 修飾詞不能用在相同的符號上。 變數的儲存體依處理序或應用程式定義域而存在。  
  
 如需詳細資訊，請參閱 [appdomain](../../cpp/appdomain.md) 和 [處理序](../../cpp/process.md)。  
  
 下列範例會產生 C2388：  
  
```  
// C2388.cpp  
// compile with: /clr /c  
__declspec(process) __declspec(appdomain) int i;   // C2388  
__declspec(appdomain) int i;   // OK  
```