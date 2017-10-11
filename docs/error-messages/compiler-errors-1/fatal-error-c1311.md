---
title: "嚴重錯誤 1311 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1311
dev_langs:
- C++
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 9aeb63e041ddfe26a8fc47afc838f2f5c3ce35d6
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

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
