---
title: "編譯器錯誤 C2415 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2415
dev_langs: C++
helpviewer_keywords: C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ff0f423ec83b9951e806a2483417f3ab79f817a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2415"></a>編譯器錯誤 C2415
不適當的運算元類型  
  
 Opcode 不使用此類型的運算元。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>透過檢查下列可能原因進行修正  
  
1.  Opcode 不支援使用的運算元數目。 檢查組件語言參考手冊，以判斷正確的運算元數目。  
  
2.  較新的處理器支援與其他類型的指示。 調整[/arch （最小 CPU 架構）](../../build/reference/arch-minimum-cpu-architecture.md)選項來使用更新版本的處理器。