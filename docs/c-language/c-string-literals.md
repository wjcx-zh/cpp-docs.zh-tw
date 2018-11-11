---
title: C 字串常值
ms.date: 08/31/2018
helpviewer_keywords:
- string literals, syntax
- strings [C++], string literals
- literal strings, C
ms.assetid: 4b05523e-49a2-4900-b21a-754350af3328
ms.openlocfilehash: bd8b49645e34224cbea7e801f197bfbcbc012915
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635607"
---
# <a name="c-string-literals"></a>C 字串常值

「字串常值」是以雙引號 (**" "**) 括住、來自來源字元集的一連串字元。 字串常值用於表示代表一連串字元，結合在一起會構成 Null 結束字串。 寬字串常值的前面一律要加上字母 **L**。

## <a name="syntax"></a>語法

*string-literal*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"** *s-char-sequence*<sub>opt</sub> **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L"** *s-char-sequence*<sub>opt</sub> **"**

*s-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*

&nbsp;&nbsp;&nbsp;&nbsp;*s-char-sequence* *s-char*

*s-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;來源字元集的所有成員，但雙引號 (")、反斜線 (\\) 或新行字元除外<br/>

&nbsp;&nbsp;&nbsp;&nbsp;*escape-sequence*

## <a name="remarks"></a>備註

下列範例是簡單的字串常值：

```C
char *amessage = "This is a string literal.";
```

[逸出序列](../c-language/escape-sequences.md)表中列出的所有逸出代碼在字串常值中都是有效的。 若要在字串常值中表示雙引號，請使用逸出序列 **\\"**。 單引號 (**'**) 可以不使用逸出序列表示。 反斜線 (**\\**) 出現在字串內時，後面必須接著第二條反斜線 (**\\\\**)。 反斜線出現在行尾時，一律解譯為行接續字元。

## <a name="see-also"></a>請參閱

[C 的元素](../c-language/elements-of-c.md)
