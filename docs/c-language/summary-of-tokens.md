---
title: 語彙基元摘要
ms.date: 11/04/2016
ms.assetid: 2978cbf6-e66e-46fc-9938-caa052f2ccf7
ms.openlocfilehash: 4fdc1cf4c4e5a89cc9ecf029e64b6eb5422cd6a3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149111"
---
# <a name="summary-of-tokens"></a>語彙基元摘要

*token*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*關鍵字*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*常數*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*string-literal*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*運算子*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標點符號*

*preprocessing-token*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*header-name*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*character-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*string-literal*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*運算子標點符號*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;不可是上述任一個的每個非空白字元

*header-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\<**  *path-spec*  **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"**  *path spec*  **"**

*path-spec*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;合法的檔案路徑

*pp-number*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**.** *digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number* *digit* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number* *nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*  **e**  *sign*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*  **E**  *sign*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*  **.**

## <a name="see-also"></a>另請參閱

[語彙文法](../c-language/lexical-grammar.md)
