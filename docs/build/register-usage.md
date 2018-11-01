---
title: 暫存器使用方式
ms.date: 11/04/2016
ms.assetid: ce58e2cf-afd3-4068-980e-28a209298265
ms.openlocfilehash: fa04318ad4af298f300fbbbad8c01d0df9500ec7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629979"
---
# <a name="register-usage"></a>暫存器使用方式

X64 架構提供 16 一般用途的暫存器 （以下稱為整數暫存器），以及 16 的 XMM/ymm 暫存註冊可供浮點數的使用。 動態暫存器是臨時暫存器，由呼叫者假設為跨呼叫終結。 需要靜態暫存器才能跨函式呼叫保留其值，且靜態暫存器必須由被呼叫者 (如果使用的話) 儲存。

## <a name="register-volatility-and-preservation"></a>變動性和保留暫存器

下表描述如何跨函式呼叫使用每一個暫存器：

||||
|-|-|-|
|登錄|狀態|用法|
|RAX|動態|傳回值暫存器|
|RCX|動態|第一個整數引數|
|RDX|動態|第二個整數引數|
|R8|動態|第三個整數引數|
|R9|動態|第四個整數引數|
|R10:R11|動態|必須由呼叫者視需要保留；在 syscall/sysret 指令中使用|
|R12:R15|靜態|必須由被呼叫者保留|
|RDI|靜態|必須由被呼叫者保留|
|RSI|靜態|必須由被呼叫者保留|
|RBX|靜態|必須由被呼叫者保留|
|RBP|靜態|必須用作框架指標；必須由被呼叫者保留|
|RSP|靜態|堆疊指標|
|XMM0, YMM0|動態|第一個 FP 引數；使用 `__vectorcall` 時的第一個向量類型引數|
|XMM1, YMM1|動態|第二個 FP 引數；使用 `__vectorcall` 時的第二個向量類型引數|
|XMM2, YMM2|動態|第三個 FP 引數；使用 `__vectorcall` 時的第三個向量類型引數|
|XMM3, YMM3|動態|第四個 FP 引數；使用 `__vectorcall` 時的第四個向量類型引數|
|XMM4, YMM4|動態|必須由呼叫者視需要保留；使用 `__vectorcall` 時的第五個向量類型引數|
|XMM5, YMM5|動態|必須由呼叫者視需要保留；使用 `__vectorcall` 時的第六個向量類型引數|
|XMM6:XMM15, YMM6:YMM15|靜態 (XMM)、動態 (YMM 的上半部分)|必須由被呼叫端保留。 YMM 暫存器必須由被呼叫者視需要保留。|

函式結束和 C 執行階段程式庫呼叫和 Windows 系統呼叫的函式項目，方向旗標在 CPU 上旗標暫存器必須清除。

## <a name="see-also"></a>另請參閱

- [x64 軟體慣例](../build/x64-software-conventions.md)
- [__vectorcall](../cpp/vectorcall.md)
- [方向旗標](../c-runtime-library/direction-flag.md)
