---
title: /DISASM
ms.date: 01/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: fb394b2266470e77c50ce5398aea961c37ac34fb
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927715"
---
# <a name="disasm"></a>/DISASM

在 DUMPBIN 輸出中列印程式碼區段的反組解碼。

## <a name="syntax"></a>語法

> **/DISASM**{ **：** \[BYTESNOBYTES|]}

### <a name="arguments"></a>引數

**BYTES**<br/>
包含指令位元組和反組解碼輸出中的解讀碼和引數。 這是預設選項。

**NOBYTES**<br/>
不會在反組解碼輸出中包含指令位元組。

## <a name="remarks"></a>備註

**/DISASM**選項會顯示檔案中程式碼區段的反組解碼。 如果檔案中有，則會使用 debug 符號。

**/DISASM**僅適用于原生、非受控的影像。 Managed 程式碼的對等工具是[ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler)。

只有[/HEADERS](headers.md) DUMPBIN 選項可用於[/gl （整個程式優化）](gl-whole-program-optimization.md)編譯器選項所產生的檔案。

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](dumpbin-options.md)
