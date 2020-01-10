---
title: IF1 和 IF2
ms.date: 11/21/2019
f1_keywords:
- IF2
- IF1
helpviewer_keywords:
- IF2 directive
- IF2 directive
ms.assetid: a0f75564-b51b-4e39-ad3b-f7421e7ecad6
ms.openlocfilehash: 60f8b0dcedb61ac06de929aff300845e342d7cfc
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317314"
---
# <a name="if1-and-if2"></a>IF1 和 IF2

**IF1**區塊會在第一次元件傳遞時評估。

如果**OPTION： SETIF2**為**TRUE**，則會在每個元件階段評估**IF2**區塊。

## <a name="syntax"></a>語法

> **IF1;;**

> **IF2;;**

## <a name="remarks"></a>備註

如需完整語法[，請參閱](if-masm.md)。

不同于5.1 版，MASM 6.1 和更新版本會在第一次傳遞時執行大部分的工作，然後視需要執行多個後續的傳遞。 相反地，MASM 5.1 一律會在兩個來源階段中組合。 因此，您可能需要修改或刪除 MASM 6.1 和更新版本下的部分傳遞相依結構。

### <a name="two-pass-directives"></a>兩階段指示詞

為了確保相容性，MASM 6.1 和更新版本支援參考兩個階段的5.1 指示詞。 其中包括 **。ERR1**， **.ERR2**、 **IF1**、 **IF2**、 **ELSEIF1**和**ELSEIF2**。 針對第二階段的結構，您必須指定[選項 SETIF2](option-masm.md)。 如果沒有**OPTION SETIF2**，則**IF2**和 **.ERR2**指示詞會造成錯誤：

```output
.ERR2 not allowed : single-pass assembler
```

MASM 6.1 和更新版本會以不同方式處理第一階段的結構。 它會將視為 **。ERR1**指示詞為 **。ERR**和**IF1**指示**詞，如同。**

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
