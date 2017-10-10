---
title: "編譯器錯誤 C2097 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d6955a610e3109c3b16edf96913be4503ee4c647
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2097"></a>編譯器錯誤 C2097
不正確的初始化  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  使用非常數值變數的初始化。  
  
2.  簡短的位址與長的位址來初始化。  
  
3.  初始化的區域結構、 等位或陣列時，使用非常數運算式編譯**/Za**。  
  
4.  包含逗號運算子的運算式進行初始化。  
  
5.  初始化運算式不是常數和符號。
