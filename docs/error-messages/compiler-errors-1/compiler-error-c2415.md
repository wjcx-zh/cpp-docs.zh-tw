---
title: 編譯器錯誤 C2415 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2415
dev_langs:
- C++
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ad06cdf891c9b958f6cf08e724f4003a8507c2d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198543"
---
# <a name="compiler-error-c2415"></a>編譯器錯誤 C2415
不適當的運算元類型  
  
 Opcode 不使用此類型的運算元。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  Opcode 不支援使用的運算元數目。 檢查組件語言參考手冊，以判斷正確的運算元數目。  
  
2.  較新的處理器支援與其他類型的指示。 調整[/arch （最小 CPU 架構）](../../build/reference/arch-minimum-cpu-architecture.md)選項來使用更新版本的處理器。