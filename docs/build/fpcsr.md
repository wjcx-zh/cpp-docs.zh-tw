---
title: FpCsr
ms.date: 11/04/2016
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
ms.openlocfilehash: 018ce39a194d5153f73fa452990844362190e6bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472811"
---
# <a name="fpcsr"></a>FpCsr

註冊狀態也會包含 x87 FPU 控制字組。 呼叫慣例會要求此暫存器為靜態。

X87 FPU 控制字組暫存器設為下列的標準值開頭的程式執行：

```
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)
FPCSR[7]: Reserved - 0
FPCSR[8:9]: Precision Control - 10B (double precision)
FPCSR[10:11]: Rounding  control - 0 (round to nearest)
FPCSR[12]: Infinity control - 0 (not used)
```

修改任何 fpcsr 欄位被呼叫端必須將它們還原，然後傳回給其呼叫端。 此外，修改這些欄位的任何呼叫端必須將它們還原至其標準的值之前叫用被呼叫端，除非由合約被呼叫端必須要有修改過的值。

有兩個規則的例外狀況為非變動性有關的控制旗標：

1. 在函式中指定的函式的文件的目的為修改靜態 FpCsr 旗標。

1. 當它是可以證明正確，這些規則的違規會導致程式的行為/意義和這些規則都不違反規則的程式，例如，透過整個程式分析與相同的。

## <a name="see-also"></a>另請參閱

[呼叫慣例](../build/calling-convention.md)