---
title: "浮點支援對舊版程式碼 （Visual c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 130b6efb1c05775cd7859144d91a30051fb4ca53
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="floating-point-support-for-older-code-visual-c"></a>舊版程式碼的浮點支援 (Visual C++)
MMX 和浮點的堆疊暫存器 (MM0-MM7/ST0-ST7) 會保留在內容切換。  對這些暫存器沒有明確呼叫慣例。  核心模式程式碼中嚴格禁止您使用這些暫存器。  
  
## <a name="see-also"></a>請參閱  
 [呼叫慣例](../build/calling-convention.md)