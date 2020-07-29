---
title: 複合陳述式 (C)
ms.date: 11/04/2016
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
ms.openlocfilehash: 93f7fd24049c744874fb0ab3bda37eedef3a139a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200578"
---
# <a name="compound-statement-c"></a>複合陳述式 (C)

複合陳述式（也稱為「區塊」）通常會顯示為另一個語句的主體，例如 **`if`** 語句。 [宣告和類型](../c-language/declarations-and-types.md)會描述可能出現在複合陳述式開頭的宣告形式和意義。

## <a name="syntax"></a>語法

*複合陳述式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{宣告** *-列出*<sub>opt</sub> *語句清單*<sub>opt</sub> **}**

*declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*清點*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *宣告*

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-list* *陳述式*

如果出現宣告，則必須位於任何陳述式前面。 在複合陳述式開頭宣告之每個識別項的範圍，都會從其宣告點延伸至區塊結尾。 除非內部區塊中存在相同識別項的宣告，否則都可在整個區塊中看見此範圍。

除非使用、或明確宣告，否則複合陳述式中的識別碼會假設為， **`auto`** 但函式 **`register`** **`static`** **`extern`** 除外，只能是 **`extern`** 。 您可以 **`extern`** 在函式宣告中省略規範，函數仍然會是 **`extern`** 。

如果在具有儲存類別的複合陳述式中宣告變數或函式，則不會配置儲存體，也不允許初始化 **`extern`** 。 宣告會參考其他位置所定義的外部變數或函式。

在具有或關鍵字的區塊中宣告的變數會重新配置， **`auto`** **`register`** 並視需要在每次輸入複合陳述式時初始化。 這些變數不是在複合陳述式結束之後定義。 如果在區塊內宣告的變數具有 **`static`** 屬性，則變數會在程式執行開始時初始化，並在整個程式中保留其值。 如需的詳細資訊，請參閱[儲存體類別](../c-language/c-storage-classes.md) **`static`** 。

這個範例將示範複合陳述式：

```
if ( i > 0 )
{
    line[i] = x;
    x++;
    i--;
}
```

在這個範例中，如果 `i` 大於 0，則複合陳述式內的所有陳述式會依序執行。

## <a name="see-also"></a>另請參閱

[陳述式](../c-language/statements-c.md)
