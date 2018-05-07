---
title: 編譯器警告 （層級 2 和 3） C4008 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4008
dev_langs:
- C++
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4cdc88f222f9e5ce3829a63c131c955ce2abdd7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>編譯器警告 (層級 2 和 3) C4008
'identifier': 已忽略 'attribute' 屬性  
  
 編譯器已忽略函式 (層級 3 警告) 或資料 (層級 2 警告) 的 `__fastcall`、 **static**或 **inline** 屬性。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  具有資料的`__fastcall` 屬性。  
  
2.  具有**inline** 函式的 **static** 或 **inline** 屬性。