---
title: "ARM Assembler Command-Line Reference | Microsoft Docs"
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
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ARM Assembler Command-Line Reference
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這篇文章提供有關 Microsoft ARM 組譯工具的命令列資訊 *armasm*，它會將 ARMv7 的捲動方塊組件的語言編譯成 Microsoft 實作的通用物件檔案格式 \(COFF\)。  連結器可以將連結 COFF 物件 ARM 組譯工具，或是加上由管理員所建立的物件程式庫的 c 編譯器產生的程式碼的程式碼。  
  
## 語法  
  
```  
armasm [[options]] sourcefile objectfile  
```  
  
```  
armasm [[options]] -o objectfile sourcefile  
```  
  
#### 參數  
 `options`  
 \-錯誤`filename`  
 重新導向錯誤和警告訊息，以`filename`。  
  
 \-i`dir[;dir]`  
 將指定的目錄加入至包含搜尋路徑中。  
  
 \-預先定義`directive`  
 指定組、 SETL 或集合的指示詞，以預先定義的符號。  範例：**armasm.exe \-predefine "COUNT SETA 150" source.asm**。  如需詳細資訊，請參閱[ARM 組譯工具手冊](http://go.microsoft.com/fwlink/?LinkId=246102)。  
  
 \-nowarn  
 停用所有警告訊息。  
  
 \-略過`warning`  
 停用指定的警告。  可能的值，請參閱\] 區段的相關警告。  
  
 \-說明  
 列印命令列說明訊息。  
  
 \-電腦`machine`  
 指定要在 PE 標頭中設定的電腦類型。  預設值為`machine`是：   
**ARM**\-\-將 IMAGE\_FILE\_MACHINE\_ARMNT 設定的電腦類型。  這是預設值。   
**THUMB**\-\-將 IMAGE\_FILE\_MACHINE\_THUMB 設定的電腦類型。  
  
 \-oldit  
 產生的 ARMv7 樣式 IT 區塊。  根據預設，ARMv8 相容，就會產生 IT 區塊。  
  
 \-透過`filename`  
 閱讀其他命令列引數，從`filename`。  
  
 \-16  
 組合為 16 位元的捲動方塊指令的來源。  這是預設值。  
  
 \-32  
 為 32 位元 ARM 指令組合來源。  
  
 \-g  
 產生偵錯資訊。  
  
 \-errorReport：`option`  
 指定如何內部的組譯工具將錯誤報告給 Microsoft。  預設值為`option`是：   
**none**\-\-不傳送報告。  
**prompt**會提示使用者立即傳送報告。  
**queue**會提示使用者在下次系統管理員登入時傳送報告。  這是預設值。   
**send**\-自動傳送報告。  
  
 `sourcefile`  
 原始程式檔的名稱。  
  
 `objectfile`  
 物件 \(輸出\) 檔案的名稱。  
  
 下列範例會示範如何使用 armasm 在典型的案例。  首先，使用 armasm 來建置組件語言 \(.asm\) 來原始程式檔 \(.obj\) 檔案。  然後使用 CL 命令列 c 編譯器來編譯 \(.c 轉\) 的原始程式檔，也指定連結 ARM 物件檔案的連結器選項。  
  
 **armasm myasmcode.asm \-o myasmcode.obj**  
  
 **cl myccode.c \/link myasmcode.obj**  
  
## 請參閱  
 [ARM Assembler Diagnostic Messages](../../assembler/arm/arm-assembler-diagnostic-messages.md)   
 [ARM Assembler Directives](../../assembler/arm/arm-assembler-directives.md)