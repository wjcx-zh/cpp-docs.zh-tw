---
title: ARM 組合程式診斷訊息
ms.date: 08/30/2018
f1_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
helpviewer_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
ms.openlocfilehash: 72c1ea64501ef8104fee9bdf914a1464c07c3b76
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449221"
---
# <a name="arm-assembler-diagnostic-messages"></a>ARM 組合程式診斷訊息

Microsoft ARM 組譯工具 (*armasm*) 遇到它們時發出診斷的警告和錯誤。 這篇文章會說明最常遇到的訊息。

## <a name="syntax"></a>語法

> <em>檔名</em> **(** <em>行號</em> **):** \[**錯誤**|**警告**] **A**<em>數目</em> **:** *訊息*

## <a name="diagnostic-messages---errors"></a>診斷訊息-錯誤

> A2193： 此指令會產生無法預期的行為

ARM 架構無法保證這個指令執行時，會發生什麼事。  如需有關此指令的定義完善的形式的詳細資訊，請參閱[ARM 架構參考手冊](https://go.microsoft.com/fwlink/p/?linkid=246464)。

```asm
    ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior
```

> A2196： 無法以 16 位元編碼指令

指定的指令無法編碼為 16 位元 Thumb 指令。  指定 32 位元的指示，或重新排列帶入範圍的 16 位元指令的目標標籤的程式碼。

組譯工具可能會嘗試編碼 16 位元中的分支，並發生此錯誤，即使 encodable 32 位元分支。 您可以使用來解決這個問題`.W`規範，以明確標記為 32 位元分支。

```asm
    ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits

    B.W label             ; OK
    B.N label             ; A2196: instruction cannot be encoded in 16 bits
    SPACE 10000
label
```

> A2202:不允許捲動方塊區域中的前 UAL 指示語法

捲動方塊的程式碼必須使用統一的組合器語言 」 (UAL) 語法。  不會再接受舊語法

```asm
    ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region
    ADDSEQ r0, r1         ; OK
```

> A2513:旋轉必須是偶數

在 ARM 模式中，沒有指定常數的替代語法。  反而比撰寫`#<const>`，您可以撰寫`#<byte>,#<rot>`，表示取得旋轉值的常數值`<byte>`向右`<rot>`。  當您使用此語法時，您必須進行的值`<rot>`甚至。

```asm
    MOV r0, #4, #2       ; OK
    MOV r0, #4, #1       ; A2513: Rotation must be even
```

> A2557:若要將回寫的位元組數目不正確

NEON 結構上，載入和儲存指示 (`VLDn`， `VSTn`)，沒有指定回寫到基底的暫存器的替代語法。  而不是位址後面放一個驚嘆號 （！），您可以指定 即時運算值，指出要加入至基底的暫存器的位移。  如果您使用此語法，您必須指定確切的已載入或儲存指令的位元組數目。

```asm
    VLD1.8 {d0-d3}, [r0]!         ; OK
    VLD1.8 {d0-d3}, [r0], #32     ; OK
    VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back
```

## <a name="diagnostic-messages---warnings"></a>診斷訊息-警告

> A4228:對齊值超出區域的對齊方式;不保證的對齊方式

中指定的對齊`ALIGN`指示詞括住的對齊大於`AREA`。  如此一來，「 組合器 」 無法保證`ALIGN`指示詞會被接受。

若要修正此問題，您可以指定`AREA`指示詞`ALIGN`等於或大於所需的對齊方式的屬性。

```asm
AREA |.myarea1|
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed

AREA |.myarea2|,ALIGN=3
ALIGN 8           ; OK
```

> A4508:此旋轉的常數的使用已被取代

在 ARM 模式中，沒有指定常數的替代語法。  反而比撰寫`#<const>`，您可以撰寫`#<byte>,#<rot>`，表示取得旋轉值的常數值`<byte>`向右`<rot>`。  在某些內容中，ARM 已取代這些旋轉的常數的使用。 在這些情況下，使用 basic`#<const>`語法改。

```asm
    ANDS r0, r0, #1                ; OK
    ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated
```

> A4509:這種形式的條件式指示已被取代

這種形式的條件式指示已被取代的 ARM ARMv8 架構中。 我們建議您變更程式碼以使用條件式分支。 若要查看仍受到支援的條件式的指示，請參閱[ARM 架構參考手冊](https://go.microsoft.com/fwlink/p/?linkid=246464)。

這個警告不是時，就發出 **-oldit**使用命令列參數。

```asm
    ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated
```

## <a name="see-also"></a>另請參閱

[ARM 組譯工具命令列參考](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[ARM 組譯工具指示詞](../../assembler/arm/arm-assembler-directives.md)<br/>
