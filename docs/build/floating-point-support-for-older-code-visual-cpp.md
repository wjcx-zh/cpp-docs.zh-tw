---
title: 浮點支援對舊版程式碼 （Visual c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd7cbf955fbf795d06d9cd2448d0736dc435f3b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367156"
---
# <a name="floating-point-support-for-older-code-visual-c"></a>舊版程式碼的浮點支援 (Visual C++)
MMX 和浮點的堆疊暫存器 (MM0-MM7/ST0-ST7) 會保留在內容切換。  對這些暫存器沒有明確呼叫慣例。  核心模式程式碼中嚴格禁止您使用這些暫存器。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫慣例](../build/calling-convention.md)