---
title: "ARM 組合程式指示詞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6d42e099ecf8d3630e54eeb629bb3f9f46fa363
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="arm-assembler-directives"></a>ARM 組合程式指示詞
大部分的情況下，Microsoft ARM 組件會使用 ARM 組譯語言，而其記錄在第 7 章[ARM 組譯工具指南](http://go.microsoft.com/fwlink/p/?linkid=246102)。 不過，有些組件指示詞的 Microsoft 實作，ARM 組件指示詞而有所不同。 本文說明的差異。  
  
## <a name="microsoft-implementations-of-arm-assembly-directives"></a>ARM 組件指示詞的 Microsoft 實作  
 區域  
 Microsoft ARM 組件支援這些區域屬性： 對齊程式碼、 CODEALIGN、 資料、 NOINIT、 READONLY、 READWRITE、 縮圖、 ARM。  
  
 捲動方塊和 ARM 以外的所有工作中所述[ARM 組譯工具指南](http://go.microsoft.com/fwlink/p/?linkid=246102)。  
  
 在 Microsoft ARM 組件中，捲動方塊表示程式碼區段包含捲動方塊程式碼，以及為程式碼區段的預設值。  ARM 表示的區段包含 ARM 程式碼。  
  
 ATTR  
 不支援。  
  
 CODE16  
 由於這表示前置 UAL Thumb 語法 Microsoft ARM 組件不允許不支援。  請改用 THUMB 指示詞，以及 UAL 語法。  
  
 一般  
 不支援的一般區域對齊的規格。  
  
 DCDO  
 不支援。  
  
 DN，QN，SN  
 不支援的類型或通道上的暫存器別名的規格。  
  
 項目  
 不支援。  
  
 EQU  
 不支援的類型定義的符號的規格。  
  
 匯出和全域  
 ```  
EXPORTsym {[type]}  
```  
  
 `sym` 是要匯出的符號。  `[type]`如果指定，可以是`[DATA]`表示符號是否指向資料或`[FUNC]`表示符號是否指向程式碼。  
  
 全域是匯出的同義字。  
  
 EXPORTAS  
 不支援。  
  
 畫面格  
 不支援。  
  
 函式和處理序  
 雖然 assembly 語法支援的自訂規格程序呼叫慣例，藉由列出暫存器儲存呼叫端和被呼叫端儲存 Microsoft ARM 組譯工具可接受的語法，但忽略暫存器清單。  組譯工具所產生的偵錯資訊支援只有預設呼叫慣例。  
  
 匯入和 EXTERN  
 ```  
IMPORT sym{, WEAK alias{, TYPE t}}  
```  
  
 `sym` 是要匯入的符號名稱。  
  
 如果是弱式`alias`指定時，它會指出`sym`是弱式外部。 如果沒有定義位於連結時，則所有參照，改為繫都結至`alias`。  
  
 如果型別`t`不指定，則`t`指出如何連結器應該嘗試解析`sym`。  這些值`t`可能會有：   
1 — 不會執行文件庫中的搜尋 `sym`  
2-執行的程式庫搜尋 `sym`  
3-`sym`別名`alias`（預設值）  
  
 EXTERN 同義匯入，不同處在於`sym`只有在它的參考目前的組件匯入。  
  
 MACRO  
 不支援使用條件碼巨集的變數。 巨集不支援參數的預設值。  
  
 NOFP  
 不支援。  
  
 選擇加入，TTL、 SUBT  
 不支援，因為 Microsoft ARM 組件不會產生清單。  
  
 PRESERVE8  
 不支援。  
  
 重新配置  
 `RELOC n` 只可以遵循指示或資料定義指示詞。 可以重新定位沒有 「 匿名符號 」。  
  
 需要  
 不支援。  
  
 REQUIRE8  
 不支援。  
  
 THUMBX  
 不支援，因為 Microsoft ARM 組件不支援捲動方塊 2EE 指令集。  
  
## <a name="see-also"></a>請參閱  
 [ARM 組合程式命令列參考](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [ARM 組譯工具診斷訊息](../../assembler/arm/arm-assembler-diagnostic-messages.md)