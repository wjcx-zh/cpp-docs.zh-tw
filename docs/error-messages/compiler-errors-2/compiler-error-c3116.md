---
title: 編譯器錯誤 C3116 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3116
dev_langs:
- C++
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fde589df31e6e3b75f9a0153d7383ab1e85ed180
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3116"></a>編譯器錯誤 C3116
'儲存體規範': 介面方法的儲存類別無效  
  
 您使用`typedef`， `register`，或`static`為介面方法的存放裝置類別。 這些儲存類別不允許在介面成員上。  
  
 下列範例會產生 C3116:  
  
```  
// C3116.cpp  
__interface ImyInterface  
{  
   static void myFunc();   // C3116  
};  
```