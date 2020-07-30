---
title: 函式主體
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
ms.openlocfilehash: 2ae73ab4ca91e06e3b6cd41166a8d05ae0857e4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229697"
---
# <a name="function-body"></a>函式主體

「函式*主體*」是複合陳述式，其中包含指定函式功能的語句。

## <a name="syntax"></a>語法

*函式定義*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *宣告子* *declaration-list*<sub>opt</sub> *compound-statement*

/\**屬性-seq*是 Microsoft 特有的\*/

*複合陳述式*：/ \* 函數主體\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{宣告** *-列出*<sub>opt</sub> *語句清單*<sub>opt</sub> **}**

除非另有指定，否則在函式主體中宣告的變數（稱為*區域變數*）具有 **`auto`** 儲存類別。 呼叫函式時，會建立區域變數儲存區並執行區域初始化。 執行控制會傳遞給*複合陳述式*中的第一個語句，並繼續直到 **`return`** 執行語句或遇到函式主體的結尾為止。 然後，控制權會回到呼叫該函式的點。

**`return`** 如果函數要傳回值，則必須執行包含運算式的語句。 如果未 **`return`** 執行任何語句，或語句不包含運算式，則函式的傳回值會是未定義的 **`return`** 。

## <a name="see-also"></a>另請參閱

[C 函式定義](../c-language/c-function-definitions.md)
