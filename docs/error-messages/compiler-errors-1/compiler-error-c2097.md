---
title: 編譯器錯誤 C2097 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa4b867c7f043d796f208fdc7100509893147daf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2097"></a>編譯器錯誤 C2097
不正確的初始化  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  使用非常數值變數的初始化。  
  
2.  簡短的位址與長的位址來初始化。  
  
3.  初始化的區域結構、 等位或陣列時，使用非常數運算式編譯 **/Za**。  
  
4.  包含逗號運算子的運算式進行初始化。  
  
5.  初始化運算式不是常數和符號。