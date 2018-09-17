---
title: 浮點支援較舊的程式碼 （Visual c + +） |Microsoft Docs
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
ms.openlocfilehash: 7285325bf1a934afcef337da318d019ec6fe375c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706806"
---
# <a name="floating-point-support-for-older-code-visual-c"></a>舊版程式碼的浮點支援 (Visual C++)

MMX 和浮點堆疊暫存器 (MM0-MM7/ST0-ST7) 會保留在內容切換。  沒有任何明確的呼叫慣例，這些暫存器。  這些暫存器使用嚴格禁止在核心模式程式碼。

## <a name="see-also"></a>另請參閱

[呼叫慣例](../build/calling-convention.md)