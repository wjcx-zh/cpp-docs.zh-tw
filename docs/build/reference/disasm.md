---
title: /DISASM
ms.date: 1/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: 10e8187e896b3922438a8cf2dafa0aec4c91f904
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272057"
---
# <a name="disasm"></a>/DISASM

列印 DUMPBIN 輸出中的程式碼區段的反組譯碼。

## <a name="syntax"></a>語法

> **/DISASM**{**:**\[**BYTES**|**NOBYTES**]}

### <a name="arguments"></a>引數

**BYTES**<br/>
包含指令的位元組以及解譯的 opcode 及引數的反組譯碼輸出中。 這是預設選項。

**NOBYTES**<br/>
不在反組譯碼輸出中包含指令的位元組。

## <a name="remarks"></a>備註

**/DISASM**選項顯示反組譯程式碼區段的檔案中。 如果它們存在檔案中，它會使用偵錯符號。

**/DISASM**應該只用在原生、 未受管理的映像上。 Managed 程式碼的對等工具是[ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler)。

只有[/HEADERS](headers.md) DUMPBIN 選項只適用於所產生的檔案上[/GL （整個程式最佳化）](gl-whole-program-optimization.md)編譯器選項。

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](dumpbin-options.md)
