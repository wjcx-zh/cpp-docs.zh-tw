---
title: 編譯器錯誤 C3553 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3553
dev_langs:
- C++
helpviewer_keywords:
- C3553
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a4ed8c2776015f9d9c6aedbe7a9da93f404f680
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3553"></a>編譯器錯誤 C3553
decltype 必須是運算式而不是類型  
  
 `decltype()` 關鍵字需要運算式作為引數，而不是類型名稱。 例如，下列程式碼片段的最後一個陳述式會產生錯誤 C3553。  
  
 `int x = 0;`  
  
 `decltype(x+1);`  
  
 `decltype(int); // C3553`