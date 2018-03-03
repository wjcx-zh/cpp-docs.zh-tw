---
title: "編譯器警告 （層級 1） C4083 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4083
dev_langs:
- C++
helpviewer_keywords:
- C4083
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c777415a35b5ac4d581434c1ede01cd98b405d00
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4083"></a>編譯器警告 （層級 1） C4083
必須是 'token';找到識別項 'identifier'  
  
 識別項，就會發生在錯誤的位置中**#pragma**陳述式。  
  
## <a name="example"></a>範例  
  
```  
// C4083.cpp  
// compile with: /W1 /LD  
#pragma warning disable:4083    // C4083  
#pragma warning(disable:4083)   //correct  
```  
  
 請檢查語法[#pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)指示詞。