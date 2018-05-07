---
title: 編譯器錯誤 C3554 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3554
dev_langs:
- C++
helpviewer_keywords:
- C3554
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4fb374e028097157ae72b621593a899af9fe2f91
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3554"></a>編譯器錯誤 C3554
'decltype' 無法和任何其他型別規範結合  
  
 您不能限制 `decltype()` 關鍵字搭配任何類型規範。 例如，下列程式碼片段會產生錯誤 C3554。  
  
```  
int x;  
unsigned decltype(x); // C3554  
```