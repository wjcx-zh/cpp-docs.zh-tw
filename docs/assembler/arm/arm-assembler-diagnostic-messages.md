---
title: "ARM Assembler Diagnostic Messages | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ARM Assembler Diagnostic Messages
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft ARM 組譯工具 \(*armasm*\) 時遇到它們便會發出診斷的警告和錯誤。  本文將告訴您最常遇到的訊息。  
  
## 語法  
  
```  
  
filename(lineno) : [error|warning] Anum: message  
```  
  
## 診斷訊息  
  
### 錯誤  
 A2193: 這個指令會產生無法預期的行為  
 ARM 架構無法保證執行此指令時，會發生什麼事。  如需定義完善的表單，此指令的詳細資訊，請參閱[ARM 架構參考手冊](http://go.microsoft.com/fwlink/?LinkId=246464)。  
  
```  
  
ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior  
  
```  
  
 A2196: 無法在 16 位元編碼指令  
 在指定的指令無法編碼成 16 位元的捲動方塊指令。  指定的 32 位元指令，或重新排列程式碼，將目標標籤擴增的 16 位元指令。  
  
 組譯工具可能會嘗試進行編碼以 16 位元的多層子目錄，並因這項錯誤，即使 32 位元分支是 encodable。  您可以解決這個問題，藉由使用`.W`規範來明確地標記為 32 位元的分支。  
  
```  
  
  ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits  
  
  B.W label             ; OK  
  B.N label             ; A2196: instruction cannot be encoded in 16 bits  
  SPACE 10000  
label  
  
```  
  
 A2202: P E UAL 指令語法不允許出現在 \[縮圖 \(地區\)  
 捲動方塊的程式碼必須使用統一的組譯工具語言 \(UAL\) 的語法。  舊語法不再被接受  
  
```  
  
ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region  
ADDSEQ r0, r1         ; OK  
  
```  
  
 A2513: 旋轉必須是偶數  
 ARM 模式中，則替代語法來指定常數。  書寫代替`#<const>`，您可以撰寫`#<byte>,#<rot>`，用來表示藉由旋轉值的常數值`<byte>`向右`<rot>`。  當您使用此語法時，您必須進行的值`<rot>`甚至。  
  
```  
  
MOV r0, #4, #2       ; OK  
MOV r0, #4, #1       ; A2513: Rotation must be even  
  
```  
  
 A2557: 上一步寫入的位元組數目不正確  
 霓虹結構中，載入和儲存的指示 \(`VLDn`， `VSTn`\)，沒有替代語法來指定要回寫至基底暫存器。  而不是地址後面加一個驚嘆號 \(\!\)，您可以指定立即的值，指出要加入至基底暫存器位移。  如果您使用此語法時，您必須指定確切的載入或儲存由指令的位元組數目。  
  
```  
  
VLD1.8 {d0-d3}, [r0]!         ; OK  
VLD1.8 {d0-d3}, [r0], #32     ; OK  
VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back  
  
```  
  
### 警告  
 A4228: 對齊值超過區對齊方式。 不保證的對齊方式  
 在所指定的對齊方式`ALIGN`指示詞的對齊封入大於`AREA`。  如此一來，組譯工具不能保證， `ALIGN`指示詞，將會套用。  
  
 若要修正這個問題，您可以指定在`AREA`指示詞`ALIGN`等於或晚於您想要的對齊方式的屬性。  
  
```  
  
AREA |.myarea1|  
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed  
  
AREA |.myarea2|,ALIGN=3  
ALIGN 8           ; OK  
  
```  
  
 A4508: 已被取代這個旋轉的常數的使用  
 ARM 模式中，則替代語法來指定常數。  書寫代替`#<const>`，您可以撰寫`#<byte>,#<rot>`，用來表示藉由旋轉值的常數值`<byte>`向右`<rot>`。  在某些情況中，ARM 已取代旋轉常數的使用。  在這些情況下，使用基本`#<const>`語法代替。  
  
```  
  
ANDS r0, r0, #1                ; OK  
ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated  
  
```  
  
 A4509: 這種形式的條件式指示已被取代  
 這種形式的條件式指示已被取代的 ARM ARMv8 架構中。  我們建議您變更使用條件式分支的程式碼。  若要查看仍然支援哪一個條件式指示，請參閱[ARM 架構參考手冊](http://go.microsoft.com/fwlink/?LinkId=246464)。  
  
 這項警告並不發出何時 `-oldit` 使用命令列參數。  
  
```  
  
ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated  
  
```  
  
## 請參閱  
 [ARM Assembler Command\-Line Reference](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [ARM Assembler Directives](../../assembler/arm/arm-assembler-directives.md)