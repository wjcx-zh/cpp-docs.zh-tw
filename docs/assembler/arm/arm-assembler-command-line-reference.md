---
title: ARM 組合程式命令列參考 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e88f35035944ee24bed0bef8733db0e2c0139c83
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685337"
---
# <a name="arm-assembler-command-line-reference"></a>ARM 組合程式命令列參考

本文章提供有關 Microsoft ARM 組譯工具的命令列資訊*armasm*，這將 ARMv7 Thumb 組件語言編譯成 Microsoft 實作的通用物件檔案格式 (COFF)。 連結器可以連結 （coff） 的程式碼與產生 ARM 組譯工具或 C 編譯器，以及管理員所建立的物件程式庫物件。

## <a name="syntax"></a>語法

> **armasm** [*選項*] *sourcefile* *objectfile*
> **armasm** [*選項*] **-o** *objectfile* *sourcefile*

### <a name="parameters"></a>參數

*options*<br/>
零個或多個項目組合：

- **-錯誤***檔名*<br/>
   將錯誤和警告訊息，以重新導向*filename*。

- **-i** *dir*[**;**<em>dir</em>]<br/>
   加入包含搜尋路徑中指定的目錄。

- **-預先定義***指示詞*<br/>
   指定預先定義符號的 SETA、 SETL 或設定指示詞。<br/>
   範例： **armasm.exe-預先定義"COUNT SETA 150"source.asm**<br/>
   如需詳細資訊，請參閱 < [ARM 編譯器 armasm 參考指南](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html)。

- **-nowarn**<br/>
   停用所有警告訊息。

- **-忽略***警告*<br/>
   停用指定的警告。 如需可能的值，請參閱有關警告的章節。

- **-help**<br/>
   列印命令列說明訊息。

- **-machine** *機器*<br/>
   指定設定的 PE 標頭中的機器類型。  可能值為*機器*是：<br/>
   **ARM**— IMAGE_FILE_MACHINE_ARMNT 設定機器類型。 這是預設值。<br/>
   **THUMB**— IMAGE_FILE_MACHINE_THUMB 設定機器類型。

- **-oldit**<br/>
   產生 ARMv7 樣式 IT 區塊。  根據預設，ARMv8 相容 IT 區塊所產生。

- **-透過***檔名*<br/>
   讀取其他的命令列引數，從*filename*。

- **-16**<br/>
   組合為 16 位元的 Thumb 指令的來源。  這是預設值。

- **-32**<br/>
   組合為 32 位元 ARM 指令的來源。

- **-g**<br/>
   產生偵錯資訊。

- **-errorReport:** *選項*<br/>
   指定向 Microsoft 報告錯誤的方式內部組譯工具。  可能值為*選項*是：<br/>
   **無**-不傳送報告。<br/>
   **提示字元**，提示使用者立即傳送報告。<br/>
   **佇列**，提示使用者在下一步 的管理員登入傳送報告。 這是預設值。<br/>
   **傳送**— 傳送自動報告。

*sourcefile*<br/>
原始程式檔的名稱。

*objectfile*<br/>
物件 （輸出） 檔案的名稱。

## <a name="remarks"></a>備註

下列範例示範如何使用 armasm 在典型的案例。 首先，使用 armasm 來建置組件語言來源 (.asm) 檔 (.obj) 檔案。 然後，使用 CL 命令列 C 編譯器來編譯來源 (.cpp) 檔案，並也指定連結器選項連結 ARM 物件檔案。

**armasm myasmcode.asm-o myasmcode.obj**

**cl myccode.c /link myasmcode.obj**

## <a name="see-also"></a>另請參閱

[ARM 組譯工具診斷訊息](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
[ARM 組譯工具指示詞](../../assembler/arm/arm-assembler-directives.md)<br/>
