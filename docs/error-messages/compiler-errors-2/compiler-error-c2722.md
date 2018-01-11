---
title: "編譯器錯誤 C2722 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2722
dev_langs: C++
helpviewer_keywords: C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2f8526422129b1fe114974de1c7f95cb55117d99
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2722"></a>編譯器錯誤 C2722
':: 運算子 ': 不合法的下列運算子命令。使用 '運算子 operator operator'  
  
 `operator`陳述式重新定義`::new`或`::delete`。 `new`和`delete`運算子是全域的所以範圍解析運算子 (`::`) 不具任何意義。 移除`::`運算子。