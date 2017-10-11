---
title: "編譯器錯誤 C3874 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3874
dev_langs:
- C++
helpviewer_keywords:
- C3874
ms.assetid: fd55fc05-69a7-4237-b3b7-dca1d5400b4f
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: cd30858e2118a7305583736c31b84ed56ab7095a
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3874"></a>編譯器錯誤 C3874
'function' 傳回型別應該是 'int'，而不是 'type'  
  
 函式沒有編譯器預期的傳回型別。  
  
 下列範例會產生 C3874:  
  
```  
// C3874b.cpp  
double main()  
{   // C3874  
}  
```
