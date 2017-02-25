---
title: "ARM Assembler Directives | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# ARM Assembler Directives
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

大多數的情況下，Microsoft ARM 組譯工具會使用 ARM 組件語言的一部分，它會詳細說明第 7 章[ARM 組譯工具手冊](http://go.microsoft.com/fwlink/?LinkId=246102)。  但是，ARM 組件指示詞與不同 Microsoft 的實作方式有些組件指示詞。  這篇文章說明的差異。  
  
## Microsoft 的 ARM 組件指示詞的實作  
 區域  
 Microsoft ARM 組譯工具支援這些區域屬性： 對齊，請程式碼、 CODEALIGN、 資料、 NOINIT、 唯讀、 READWRITE、 縮圖、 手臂。  
  
 捲動方塊和 ARM 以外的所有工作詳加說明，如[ARM 組譯工具手冊](http://go.microsoft.com/fwlink/?LinkId=246102)。  
  
 在 Microsoft ARM 組譯工具中，捲動方塊會指示程式碼區段包含捲動方塊的程式碼，而且是程式碼區段的預設值。  ARM 指示的區段包含手臂的程式碼。  
  
 屬性  
 不支援。  
  
 代碼 16  
 不支援，因為它表示 Microsoft ARM 組譯工具不允許預先 UAL 捲動方塊語法。  相反地，使用捲動方塊指示詞一起 UAL 語法。  
  
 一般  
 不支援的常見的區域的對齊方式的規格。  
  
 DCDO  
 不支援。  
  
 DN，QN，SN  
 不支援的型別或暫存器別名巷道規格。  
  
 項目  
 不支援。  
  
 EQU  
 不支援的型別定義的符號的規格。  
  
 匯出 」 和 「 通用  
 ```  
  
EXPORTsym {[type]}  
  
```  
  
 `sym`是要匯出的符號。  `[type]`如果指定，可以是`[DATA]` ，表示該符號指向的資料或`[FUNC]` ，表示該符號會指向的程式碼。  
  
 \[全域\] 是同義資料表來進行匯出。  
  
 EXPORTAS  
 不支援。  
  
 圖文框  
 不支援。  
  
 函式和處理序  
 雖然組件語法支援規格的自訂程序呼叫慣例，藉以是儲存檔案的呼叫端和被呼叫端儲存的暫存器 Microsoft ARM 組譯工具接受語法但會忽略暫存器清單。  偵錯資訊由組譯工具所產生的支援呼叫慣例的預設值。  
  
 匯入及外部  
 ```  
  
IMPORT sym{, WEAK alias{, TYPE t}}  
  
```  
  
 `sym`是要匯入符號的名稱。  
  
 如果弱式`alias`指定，則表示`sym`是弱式的外部。  如果沒有為它的定義位於連結時，那麼所有的參照，而是繫結至`alias`。  
  
 如果型別 `t`指定，則再`t`指示如何連結器應該嘗試解決`sym`。  這些值的`t`也有可能：   
1 — 並不會執行媒體櫃中的搜尋`sym`   
2 — 執行媒體櫃中的搜尋`sym`   
3\-`sym`為`alias` \(預設值\)  
  
 EXTERN 是匯入\] 以外的同義字`sym`在目前的組件會參考到它時，才會匯入。  
  
 巨集  
 不支援的變數，以保留條件程式碼，以確定巨集使用。  巨集不支援參數的預設值。  
  
 NOFP  
 不支援。  
  
 選擇，TTL，SUBT  
 不支援，因為 Microsoft ARM 組譯工具不會產生清單。  
  
 PRESERVE8  
 不支援。  
  
 重新配置  
 `RELOC n`只可以依照指令或資料定義指示詞。  沒有任何 「 匿名符號"能重新定位。  
  
 需要  
 不支援。  
  
 REQUIRE8  
 不支援。  
  
 THUMBX  
 不支援此因為 Microsoft ARM 組譯工具不支援的捲動方塊 2EE 指令集。  
  
## 請參閱  
 [ARM Assembler Command\-Line Reference](../../assembler/arm/arm-assembler-command-line-reference.md)   
 [ARM Assembler Diagnostic Messages](../../assembler/arm/arm-assembler-diagnostic-messages.md)