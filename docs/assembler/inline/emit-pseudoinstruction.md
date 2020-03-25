---
title: _emit 虛擬指令
ms.date: 08/30/2018
f1_keywords:
- _emit
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
ms.openlocfilehash: 8be250aadf20dc4a7dee6a0b565ece21840339d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169470"
---
# <a name="_emit-pseudoinstruction"></a>_emit 虛擬指令

**Microsoft 專屬**

**_Emit** pseudoinstruction 會在目前的文字區段中，定義目前位置的一個位元組。 **_Emit** PSEUDOINSTRUCTION 與 MASM 的[DB](../../assembler/masm/db.md)指示詞類似。

下列片段將位元組 0x4A、0x43 和 0x4B 放入程式碼：

```cpp
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B
.
.
.
__asm {
    randasm
    }
```

> [!CAUTION]
> 如果 `_emit` 會產生修改暫存器的指令，而您以最佳化編譯應用程式，則編譯器無法判斷哪些暫存器會受到影響。 例如，如果 `_emit` 產生修改**rax**暫存器的指令，則編譯器不會知道**rax**已經變更。 在內嵌組合語言程式碼執行之後，編譯器可能會對暫存器中的值做出不正確的假設。 因此，應用程式在執行時可能會表現出無法預期的行為。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[在 __asm 區塊中使用組合語言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
