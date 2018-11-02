---
title: MxCsr
ms.date: 11/04/2016
ms.assetid: 4f3c229d-0862-4733-acc7-9ed7a0b870ce
ms.openlocfilehash: d411223634aec6d11413ac1f5b1fb04dba7498e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497368"
---
# <a name="mxcsr"></a>MxCsr

註冊狀態也會包含 MxCsr。 呼叫慣例會將此註冊分成變動性的部分和靜態部分。 動態部分所組成的 6 的狀態旗標，MXCSR [0:5]，而暫存器，MXCSR [6:15] 的其餘部分會被視為靜態。

靜態部分設為下列的標準值開頭的程式執行：

```
MXCSR[6]         : Denormals are zeros - 0
MXCSR[7:12]      : Exception masks all 1's (all exceptions masked)
MXCSR[13:14]   : Rounding  control - 0 (round to nearest)
MXCSR[15]      : Flush to zero for masked underflow - 0 (off)
```

修改的任何靜態欄位 mxcsr 被呼叫端必須將它們還原，然後傳回給其呼叫端。 此外，修改這些欄位的任何呼叫端必須將它們還原至其標準的值之前叫用被呼叫端，除非由合約被呼叫端必須要有修改過的值。

有兩個規則的例外狀況為非變動性有關的控制旗標：

- 在函式中指定的函式的文件的目的為修改靜態 MxCsr 旗標。

- 當它是可以證明正確，這些規則的違規會導致程式的行為/意義和這些規則都不違反規則的程式，例如，透過整個程式分析與相同的。

除非特別說明函式的文件中做任何限制性規定可以不進行跨函式界限，變動部分的 MXCSR 狀態相關。

## <a name="see-also"></a>另請參閱

[呼叫慣例](../build/calling-convention.md)