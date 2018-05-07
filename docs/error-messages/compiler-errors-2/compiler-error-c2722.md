---
title: 編譯器錯誤 C2722 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2722
dev_langs:
- C++
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c8838ed6b2d202d58c9553a773da9653839b6c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2722"></a>編譯器錯誤 C2722
':: 運算子 ': 不合法的下列運算子命令。使用 '運算子 operator operator'  
  
 `operator`陳述式重新定義`::new`或`::delete`。 `new`和`delete`運算子是全域的所以範圍解析運算子 (`::`) 不具任何意義。 移除`::`運算子。