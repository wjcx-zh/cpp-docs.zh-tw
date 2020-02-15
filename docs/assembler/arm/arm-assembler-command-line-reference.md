---
title: ARM 組譯工具命令列參考
description: Microsoft ARM 組合器命令列選項的參考指南。
ms.date: 02/09/2020
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
ms.openlocfilehash: a63273e8d21e7a28574ec79d62c15f29ee59cd50
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257375"
---
# <a name="arm-assembler-command-line-reference"></a>ARM 組譯工具命令列參考

本文提供有關 Microsoft ARM 組合器**armasm**的命令列資訊。 **armasm**將 ARMv7 Thumb 元件語言組合成 Microsoft 的通用物件檔案格式（COFF）執行。 連結器可以連結 ARM 組合語言和 C 編譯器所產生的 COFF 程式碼物件。 它可以與管理員所建立的物件程式庫連結在一起。

## <a name="syntax"></a>語法

> **`armasm`** [*options*] *source_file* *object_file*\
> **`armasm`** [*options*] **`-o`** *object_file* *source_file*

### <a name="parameters"></a>參數

*選項*\
下列零或多個選項的組合：

- **`-errors`** *filename*\
   將錯誤和警告訊息重新導向至*filename*。

- **`-i`** *dir*[ **`;`** <em>dir</em>] \
   將指定的目錄新增至 include 搜尋路徑。

- **`-predefine`** 指示*詞\*
   指定 SETA、SETL 或 SET 指示詞以預先定義符號。
   範例： `armasm.exe -predefine "COUNT SETA 150" source.asm`\
   如需詳細資訊，請參閱[ARM 編譯器 Armasm 參考指南](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html)。

- **`-nowarn`**\
   停用所有警告訊息。

- **`-ignore`** *警告*\
   停用指定的警告。 如需可能的值，請參閱關於警告的一節。

- **`-help`**\
   列印命令列說明訊息。

- **`-machine`** *機*\
   指定要在 PE 標頭中設定的電腦類型。  *機器*的可能值為： \
   **ARM**—將電腦類型設定為 IMAGE_FILE_MACHINE_ARMNT。 此選項是預設值。
   **THUMB**—將電腦類型設定為 IMAGE_FILE_MACHINE_THUMB。

- **`-oldit`**\
   產生 ARMv7 樣式的 IT 區塊。  根據預設，會產生與 ARMv8 相容的 IT 區塊。

- **`-via`** *filename*\
   從*檔案名*讀取其他命令列引數。

- **`-16`**\
   將來源組合為16位捲動方塊指示。  這個選項是預設值。

- **`-32`**\
   將來源組合為32位 ARM 指示。

- **`-g`**\
   產生調試資訊。

- **`-errorReport:`** *選項*\
   這個選項已被取代。 從 Windows Vista 開始，錯誤報表是由[Windows 錯誤報告（WER）](/windows/win32/wer/windows-error-reporting)設定所控制。

*source_file*\
原始程式檔的名稱。

*object_file*\
物件（輸出）檔案的名稱。

## <a name="remarks"></a>備註

下列範例示範如何在一般案例中使用 armasm。 首先，使用 armasm 來建立元件語言來源（.asm）檔案至物件（.obj）檔案。 然後，使用 CL 命令列 C 編譯器來編譯來源（.c）檔案，並同時指定連結器選項來連結 ARM 物件檔案。

```cmd
armasm myasmcode.asm -o myasmcode.obj
cl myccode.c /link myasmcode.obj
```

## <a name="see-also"></a>另請參閱

[ARM 組譯工具診斷訊息](../../assembler/arm/arm-assembler-diagnostic-messages.md)\
[ARM 組合器指示詞](../../assembler/arm/arm-assembler-directives.md)
