---
title: ARM 組合程式指示詞 |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c37e010caa6c7cfb44ddaf2f7dd1e28bbb5c291
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717700"
---
# <a name="arm-assembler-directives"></a>ARM 組合程式指示詞

大部分的情況下，Microsoft ARM 組譯工具會使用 ARM 組譯語言，所述[ARM 編譯器 armasm 參考指南](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html)。 不過，Microsoft 實作的某些組件指示詞的 ARM 組件指示詞而有所不同。 這篇文章說明的差異。

## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Microsoft 實作的 ARM 組件指示詞

- 區域

   Microsoft ARM 組譯工具支援下列`AREA`屬性： `ALIGN`， `CODE`， `CODEALIGN`， `DATA`， `NOINIT`， `READONLY`， `READWRITE`， `THUMB`， `ARM`。

   以外的所有`THUMB`並`ARM`工作中所述[ARM 編譯器 armasm 參考指南](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html)。

   在 Microsoft ARM 組譯工具中，`THUMB`指出`CODE`一節包含捲動方塊的程式碼，而且是預設值`CODE`區段。  `ARM` 表示區段包含 ARM 程式碼。

- ATTR

   不支援。

- 代碼 16

   不支援，因為這表示前 UAL Thumb 語法中，不允許 Microsoft ARM 組譯工具。  使用`THUMB`相反地，以及 UAL 語法指示詞。

- 一般

   不支援的常見區域對齊的規格。

- DCDO

   不支援。

- `DN`, `QN`, `SN`

   不支援的型別或通道上的暫存器別名規格。

- 項目

   不支援。

- EQU

   不支援的類型定義的符號的規格。

- `EXPORT` 和 `GLOBAL`

   指定匯出使用下列語法：

   > **匯出**|**GLOBAL** <em>sym</em>{**[**<em>類型</em>**]**}

   *sym*是要匯出的符號。  [*型別*]，如果指定，可以是`[DATA]`表示符號是否指向資料或`[FUNC]`表示符號是否指向程式碼。 `GLOBAL` 是的同義字`EXPORT`。

- EXPORTAS

   不支援。

- 畫面格

   不支援。

- `FUNCTION` 和 `PROC`

   雖然 assembly 語法支援的自訂規格程序的呼叫慣例，藉由列出暫存器儲存呼叫端和被呼叫端儲存的 Microsoft ARM 組譯工具會接受語法，但會略過註冊清單。  由 「 組合器 」 所產生的偵錯資訊支援只的預設呼叫慣例。

- `IMPORT` 和 `EXTERN`

   指定匯入使用此語法：

   > **匯入**|**EXTERN** *sym*{**，弱式***別名*{**，型別***t*}}

   *sym*是要匯入的符號名稱。

   如果`WEAK`*別名*指定時，它會指出*sym*是弱式外部。 如果沒有為它的定義位於連結時，則所有參考都改為繫都結至*別名*。

   如果`TYPE` *t*指定*t*指出如何連結器應該嘗試解決*sym*。  這些值*t*可能會有：

   |值|描述|
   |-|-|
   |1|不會執行的程式庫搜尋*符號*|
   |2|執行程式庫搜尋*符號*|
   |3|*sym*為其別名*別名*（預設值）|

   `EXTERN` 是的同義字`IMPORT`，只不過*sym*有參考它目前的組件時，才會匯入。

- MACRO

   不支援的巨集的條件程式碼的變數使用。 巨集不支援參數的預設值。

- NOFP

   不支援。

- `OPT`, `TTL`, `SUBT`

   不支援，因為 Microsoft ARM 組譯工具不會產生清單。

- PRESERVE8

   不支援。

- 重新配置

   `RELOC n` 只能遵循指示或資料定義指示詞。 沒有可以重新放置任何 「 匿名符號 」。

- 需要

   不支援。

- REQUIRE8

   不支援。

- THUMBX

   不支援，因為 Microsoft ARM 組譯工具不支援捲動方塊 2EE 指令集。

## <a name="see-also"></a>另請參閱

[ARM 組譯工具命令列參考](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[ARM 組譯工具診斷訊息](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
