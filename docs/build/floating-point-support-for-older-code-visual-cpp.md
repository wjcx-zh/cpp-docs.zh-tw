---
title: 舊版程式碼的浮點支援 (Visual C++)
ms.date: 11/04/2016
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
ms.openlocfilehash: 2340a4d136dee3438a47ce06793ed9274035250d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509639"
---
# <a name="floating-point-support-for-older-code-visual-c"></a>舊版程式碼的浮點支援 (Visual C++)

MMX 和浮點堆疊暫存器 (MM0-MM7/ST0-ST7) 會保留在內容切換。  沒有任何明確的呼叫慣例，這些暫存器。  這些暫存器使用嚴格禁止在核心模式程式碼。

## <a name="see-also"></a>另請參閱

[呼叫慣例](../build/calling-convention.md)