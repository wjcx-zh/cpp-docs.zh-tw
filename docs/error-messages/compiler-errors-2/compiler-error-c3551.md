---
title: 編譯器錯誤 C3551 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3551
dev_langs:
- C++
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f9f69adcf071415d3c1760294bdaaaec7b71f8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3551"></a>編譯器錯誤 C3551
"必須是晚期指定的傳回類型"  
  
 如果您使用 `auto` 關鍵字作為函式之傳回類型的預留位置，則必須提供晚期指定的傳回類型。 在下列範例中， `myFunction` 函式的晚期指定的傳回類型是一個指標，而這個指標指向類型 `int`之四個項目的陣列。  
  
```  
auto myFunction()->int(*)[4];   
```  
  
## <a name="see-also"></a>另請參閱  
 [auto](../../cpp/auto-cpp.md)