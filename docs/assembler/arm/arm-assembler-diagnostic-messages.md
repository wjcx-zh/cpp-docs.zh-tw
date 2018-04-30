---
title: ARM 組合程式診斷訊息 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1616b4bd9c4b64e771ec537a1b8cd7b582702222
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="arm-assembler-diagnostic-messages"></a>ARM 組合程式診斷訊息
Microsoft ARM 組譯工具 (*armasm*) 時，會發出診斷警告和錯誤遇到它們。 這篇文章描述最常遇到的訊息。  
  
## <a name="syntax"></a>語法  
  
```  
  
filename(lineno) : [error|warning] Anum: message  
```  
  
## <a name="diagnostic-messages"></a>診斷訊息  
  
### <a name="errors"></a>錯誤  
 A2193： 這個指令會產生無法預期的行為  
 ARM 架構無法保證執行這個指令時，會發生什麼事。  如需有關此指令妥善定義表單的詳細資訊，請參閱[ARM 架構參考手冊](http://go.microsoft.com/fwlink/p/?linkid=246464)。  
  
```  
  
ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior  
  
```  
  
 A2196： 無法在 16 位元編碼指令  
 指定的指令無法編碼為 16 位元 Thumb 指示。  指定的 32 位元指令，或重新排列範圍的 16 位元指令中帶入目標標籤的程式碼。  
  
 組譯工具可能會嘗試編碼 16 位元中的分支和失敗，發生下列錯誤，即使 encodable 32 位元分支。 您可以使用來解決這個問題`.W`規範，以明確標記為 32 位元分支。  
  
```  
  
  ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits  
  
  B.W label             ; OK  
  B.N label             ; A2196: instruction cannot be encoded in 16 bits  
  SPACE 10000  
label  
  
```  
  
 捲動方塊區域中不允許 A2202: Pre UAL 指示語法  
 捲動方塊程式碼必須使用統一的組譯工具語言 」 (UAL) 語法。  無法再接受舊語法  
  
```  
  
ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region  
ADDSEQ r0, r1         ; OK  
  
```  
  
 A2513： 旋轉必須是偶數  
 在 ARM 模式中，沒有指定常數替代語法。  反而比撰寫`#<const>`，您可以撰寫`#<byte>,#<rot>`，用來表示取得旋轉值的常數值`<byte>`向右旋轉`<rot>`。  當您使用此語法時，您必須進行的值`<rot>`甚至。  
  
```  
  
MOV r0, #4, #2       ; OK  
MOV r0, #4, #1       ; A2513: Rotation must be even  
  
```  
  
 A2557： 的回寫的位元組數目不正確  
 NEON 結構載入和儲存指令 (`VLDn`， `VSTn`)，沒有指定基底暫存器的回寫替代語法。  而不是位址後面放一個驚嘆號 （！），您可以指定一個立即的值，指出要加入至基底暫存器的位移。  如果您使用此語法，您必須指定確切的已載入或儲存指令的位元組數目。  
  
```  
  
VLD1.8 {d0-d3}, [r0]!         ; OK  
VLD1.8 {d0-d3}, [r0], #32     ; OK  
VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back  
  
```  
  
### <a name="warnings"></a>警告  
 A4228： 對齊值超過區域對齊。不保證的對齊方式  
 中指定的對齊方式`ALIGN`指示詞大於封閉式對齊`AREA`。  如此一來，「 組合器 」 無法保證`ALIGN`指示詞會接受一個。  
  
 若要修正此問題，您可以指定上`AREA`指示詞`ALIGN`等於或大於所要的對齊方式的屬性。  
  
```  
  
AREA |.myarea1|  
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed  
  
AREA |.myarea2|,ALIGN=3  
ALIGN 8           ; OK  
  
```  
  
 A4508： 這個旋轉的常數的使用已被取代  
 在 ARM 模式中，沒有指定常數替代語法。  反而比撰寫`#<const>`，您可以撰寫`#<byte>,#<rot>`，用來表示取得旋轉值的常數值`<byte>`向右旋轉`<rot>`。  在某些內容中，ARM 已取代這些旋轉的常數的使用。 在這些情況下，使用基本`#<const>`語法改為。  
  
```  
  
ANDS r0, r0, #1                ; OK  
ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated  
  
```  
  
 A4509： 這種形式的條件式指示已被取代  
 這種形式的條件式指示已被取代的 ARM ARMv8 架構中。 我們建議您變更程式碼以使用條件式分支。 若要查看哪些條件指示仍受到支援，請參閱[ARM 架構參考手冊](http://go.microsoft.com/fwlink/p/?linkid=246464)。  
  
 不是這項警告時，就發出`-oldit`使用命令列參數。  
  
```  
  
ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [ARM 組合程式命令列參考](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [ARM 組譯工具指示詞](../../assembler/arm/arm-assembler-directives.md)