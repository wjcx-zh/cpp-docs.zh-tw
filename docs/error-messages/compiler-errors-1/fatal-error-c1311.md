---
title: 嚴重錯誤 1311 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1311
dev_langs:
- C++
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53b3759a5fec4b072f9a9b300670d61cb0d101c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1311"></a>嚴重錯誤 1311
COFF 格式無法以靜態方式初始化 'var' 的位址數目 （位元組)  
  
 其值不編譯時期已知的位址不能以靜態方式指派給變數，其型別具有少於四個位元組的儲存體。  
  
 會發生此錯誤的程式碼，否則為有效的 c + +。  
  
 下列範例示範了一種可能會造成 C1311 的情況。  
  
```  
char c = (char)"Hello, world";   // C1311  
char *d = (char*)"Hello, world";   // OK  
```