---
title: /DISASM
ms.date: 1/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: 77f6f05029ec4480afb2180eab0bb57838d643a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462942"
---
# <a name="disasm"></a>/DISASM

列印 DUMPBIN 輸出中的程式碼區段的反組譯碼。

## <a name="syntax"></a>語法

> **/DISASM**{**:**\[**位元組**|**NOBYTES**]}

### <a name="arguments"></a>引數

**BYTES**<br/>
包含指令的位元組以及解譯的 opcode 及引數的反組譯碼輸出中。 這是預設選項。

**NOBYTES**<br/>
不在反組譯碼輸出中包含指令的位元組。

## <a name="remarks"></a>備註

**/DISASM**選項顯示反組譯程式碼區段的檔案中。 如果它們存在檔案中，它會使用偵錯符號。

**/DISASM**應該只用在原生、 未受管理的映像上。 Managed 程式碼的對等工具是[ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler)。

只有[/HEADERS](../../build/reference/headers.md) DUMPBIN 選項只適用於所產生的檔案上[/GL （整個程式最佳化）](../../build/reference/gl-whole-program-optimization.md)編譯器選項。

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](../../build/reference/dumpbin-options.md)
