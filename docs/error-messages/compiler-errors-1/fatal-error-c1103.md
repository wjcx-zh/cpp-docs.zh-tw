---
title: 嚴重錯誤 C1103 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1103
dev_langs:
- C++
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19f991fd7449eda11651dcca4adc73190e276e35
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1103"></a>嚴重錯誤 C1103
匯入 progid 時發生嚴重錯誤: 'message'  
  
 編譯器偵測到匯入類型程式庫時發生問題。  例如，您無法使用 progid 來指定類型程式庫，同時又指定 `no_registry`。  
  
 如需詳細資訊，請參閱[#import 指示詞](../../preprocessor/hash-import-directive-cpp.md)。  
  
 下列範例會產生 C1103：  
  
```  
// C1103.cpp  
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103  
```