---
title: "ARM 組合程式命令列參考 |Microsoft 文件"
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
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2eb6b395ec8f47e820cb3184c0d88b4c91e712eb
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="arm-assembler-command-line-reference"></a>ARM 組合程式命令列參考
本文章提供有關 Microsoft ARM 組譯工具的命令列資訊*armasm*，這將 ARMv7 Thumb 組件語言編譯成 Microsoft 實作的通用物件檔案格式 (COFF)。 連結器可以將連結的程式碼 COFF 與 ARM 組譯工具或管理員所建立的物件程式庫一起 C 編譯器，所產生之物件。  
  
## <a name="syntax"></a>語法  
  
```  
armasm [[options]] sourcefile objectfile  
```  
  
```  
armasm [[options]] -o objectfile sourcefile  
```  
  
#### <a name="parameters"></a>參數  
 `options`  
 -錯誤 `filename`  
 錯誤和警告訊息，以重新導向`filename`。  
  
 -i `dir[;dir]`  
 加入包含搜尋路徑中指定的目錄。  
  
 -預先定義 `directive`  
 指定預先定義符號組、 SETL 或設定指示詞。 範例： **armasm.exe-預先定義"COUNT 組 150"source.asm**。如需詳細資訊，請參閱[ARM 組譯工具指南](http://go.microsoft.com/fwlink/p/?linkid=246102)。  
  
 -nowarn  
 停用所有警告訊息。  
  
 -忽略 `warning`  
 停用指定的警告。 如需可能的值，請參閱警告的相關章節。  
  
 -說明  
 列印命令列說明訊息。  
  
 -電腦 `machine`  
 指定在 PE 標頭中設定的電腦類型。  可能值`machine`是：  
**ARM**— IMAGE_FILE_MACHINE_ARMNT 設定的電腦類型。 這是預設值。   
**捲動方塊**— IMAGE_FILE_MACHINE_THUMB 設定的電腦類型。  
  
 -oldit  
 產生 ARMv7 樣式 IT 區塊。  根據預設，ARMv8 相容 IT 區塊所產生。  
  
 -via `filename`  
 讀取其他的命令列引數，從`filename`。  
  
 -16  
 召集來源為 16 位元捲動方塊的指令。  這是預設值。  
  
 -32  
 以 32 位元 ARM 指令組合來源。  
  
 -g  
 產生偵錯資訊。  
  
 -errorReport: `option`  
 指定如何內部組譯工具錯誤報告給 Microsoft。  可能值`option`是：   
**無**— 不傳送報告。   
**提示**— 提示使用者立即傳送報告。   
**佇列**— 提示使用者在下次系統管理員登入時傳送報告。 這是預設值。   
**傳送**— 傳送自動報告。  
  
 `sourcefile`  
 原始程式檔的名稱。  
  
 `objectfile`  
 物件 （輸出） 檔案的名稱。  
  
 下列範例會示範如何使用 armasm 在典型的案例。 首先，使用 armasm 建置的 (.obj) 檔案的組件語言來源 (.asm) 檔。 然後使用 CL 命令列 C 編譯器編譯 (.c) 的原始程式檔也指定連結器選項連結 ARM 物件檔案。  
  
 **armasm myasmcode.asm-o myasmcode.obj**  
  
 **cl myccode.c /link myasmcode.obj**  
  
## <a name="see-also"></a>請參閱  
 [ARM 組合程式診斷訊息](../../assembler/arm/arm-assembler-diagnostic-messages.md)   
 [ARM 組譯工具指示詞](../../assembler/arm/arm-assembler-directives.md)