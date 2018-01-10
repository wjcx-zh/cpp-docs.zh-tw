---
title: "編譯器錯誤 C2344 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2344
dev_langs: C++
helpviewer_keywords: C2344
ms.assetid: a84c7b37-c84e-4345-8691-c23abb2dc193
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 25a058240a72dd9b3ebafd9bafbc8b930bd2cefd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2344"></a>編譯器錯誤 C2344
align(#): 使用 align 規範必須是 2 的乘冪  
  
 使用 [align](../../cpp/align-cpp.md) 關鍵字時，您傳遞的值必須是 2 的乘冪。  
  
 例如，下列程式碼會產生 C2344，因為 3 不是 2 的乘冪：  
  
```  
// C2344.cpp  
// compile with: /c  
__declspec(align(3)) int a;   // C2344  
__declspec(align(4)) int b;   // OK  
```