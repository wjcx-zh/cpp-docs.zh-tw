---
title: "編譯器警告 （層級 1） C4615 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4615
dev_langs: C++
helpviewer_keywords: C4615
ms.assetid: 7b107c01-0da2-4e01-8b40-93813e30b94c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b00f06ee1db41adcf642e1e4a84c3695b19b0720
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4615"></a>編譯器警告 (層級 1) C4615
\#pragma 警告： 未知的使用者警告類型  
  
 無效的警告規範搭配**pragma** [警告](../../preprocessor/warning.md)。 若要解決錯誤，請使用有效的警告規範。  
  
 下列範例會產生 C4615:  
  
```  
// C4615.cpp  
// compile with: /W1 /LD  
#pragma warning(enable : 4401)   // C4615, 'enable' not valid specifier  
  
// use the code below to resolve the error  
// #pragma warning(default : 4401)  
```