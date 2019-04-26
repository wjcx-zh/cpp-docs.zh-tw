---
title: 硬體例外狀況
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [C++], hardware
- errors [C++], low-level
- errors [C++], hardware
- hardware exceptions [C++]
- low level errors
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
ms.openlocfilehash: 17775f3b2ee6dfa235c93d0bf0e3335b464aaa69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153667"
---
# <a name="hardware-exceptions"></a>硬體例外狀況

大部分可由作業系統辨識的標準例外狀況是硬體定義的例外狀況。 Windows 可辨識某些低階軟體例外狀況，不過，作業系統通常最適合處理這些例外狀況。

Windows 會將不同的處理器硬體錯誤對應到本節中的例外狀況代碼。 在某些情況下，處理器可能只會產生這些例外狀況的子集。 有關例外狀況以及發出適當例外狀況代碼的 Windows 前置處理資訊。

下表摘要說明 Windows 所辨識的硬體例外狀況：

|例外狀況代碼|例外狀況的原因|
|--------------------|------------------------|
|STATUS_ACCESS_VIOLATION|讀取或寫入無法存取的記憶體位置。|
|STATUS_BREAKPOINT|遇到硬體定義的中斷點，只能由偵錯工具使用。|
|STATUS_DATATYPE_MISALIGNMENT|在未正確對齊的位址讀取或寫入資料，例如，16 位元的實體必須在 2 個位元組的界限上對齊。 (不適用於 Intel 80*x*x86 處理器。)|
|STATUS_FLOAT_DIVIDE_BY_ZERO|除以 0.0 的浮點類型。|
|STATUS_FLOAT_OVERFLOW|超出浮點類型的最大正數。|
|STATUS_FLOAT_UNDERFLOW|超出浮點類型的最小負數範圍。|
|STATUS_FLOATING_RESEVERED_OPERAND|使用保留的浮點格式 (使用無效的格式)。|
|STATUS_ILLEGAL_INSTRUCTION|嘗試執行處理器未定義的指令碼。|
|STATUS_PRIVILEGED_INSTRUCTION|執行目前電腦模式中不允許的指令。|
|STATUS_INTEGER_DIVIDE_BY_ZERO|除以 0 的整數類型。|
|STATUS_INTEGER_OVERFLOW|嘗試進行超過整數範圍的作業。|
|STATUS_SINGLE_STEP|在單一步驟模式中執行一個指令，只能由偵錯工具使用。|

上表中列出的許多例外狀況主要是要由偵錯工具、作業系統，或其他低階程式碼處理。 除了整數和浮點數的錯誤之外，您的程式碼不應該處理這些錯誤。 因此，您通常應該使用例外狀況處理篩選條件來忽略例外狀況 (運算結果為 0)。 否則，您可以透過適當的回應來防止低階機制執行。 您可以不過，採取適當的預防措施，防止藉由這些低階錯誤，可能會影響[撰寫終止處理常式](../cpp/writing-a-termination-handler.md)。

## <a name="see-also"></a>另請參閱

[撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)<br/>
[結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)