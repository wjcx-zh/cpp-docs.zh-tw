---
title: 語彙基元摘要
ms.date: 11/04/2016
ms.assetid: 2978cbf6-e66e-46fc-9938-caa052f2ccf7
ms.openlocfilehash: 4fdc1cf4c4e5a89cc9ecf029e64b6eb5422cd6a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345132"
---
# <a name="summary-of-tokens"></a>語彙基元摘要

*token*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*關鍵字*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標識*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*常數*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*字串常值*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*操作*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標點符號*

*preprocessing-token*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標頭-名稱*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*標識*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp 編號*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*字元-常數*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*字串常值*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*運算子標點符號*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;不可是上述任一個的每個非空白字元

*標頭-名稱*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\<**  *路徑-規格*  **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;** **「*路徑規格*** ** 」    

*路徑規格*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;合法的檔案路徑

*pp 編號*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*八進位*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**.** *八進位*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number* *digit* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number* *nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*  **e**  *sign*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp 數位*  **E**  *符號*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*  **.**

## <a name="see-also"></a>請參閱

[語彙文法](../c-language/lexical-grammar.md)
