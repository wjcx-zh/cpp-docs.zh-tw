---
title: C 字元常數
ms.date: 11/04/2016
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
ms.openlocfilehash: 5d87b57726f741cc96f2180de33cae01403786ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326296"
---
# <a name="c-character-constants"></a>C 字元常數

「字元常數」是藉由將可代表字元集中的單一字元包含在單引號 (**' '**) 內所形成。 字元常數用於代表[執行字元集](../c-language/execution-character-set.md)內的字元。

## <a name="syntax"></a>語法

*字元-常數*： **'** *c-char-sequence* **'**

**L '** *c-char-sequence* **'**

*c-char 順序*： *c-char*

*c-char-sequence c-char*

*c-char*：來源字元集的所有成員，但單引號 (**'**)、反斜線 (**\\**) 或新行字元除外

*escape 順序*

*escape-sequence*: *simple-escape-sequence*

*octal-escape-sequence*

*十六進位-escape 順序*

*simple-escape-sequence*: **\a \b \f \n \r \t \v** 其中一個

**\\' \\" \\\ \\?**

*八進位-escape-序列*： **\\***八進位-數位*  

**\\**  *八進位數位八進位數位*

**\\**  *八進位數位八進位數位八進位數位*

*hexadecimal-escape-sequence*: **\x**  *hexadecimal-digit*

*hexadecimal-escape-sequence hexadecimal-digit*

## <a name="see-also"></a>請參閱

[C 常數](../c-language/c-constants.md)
