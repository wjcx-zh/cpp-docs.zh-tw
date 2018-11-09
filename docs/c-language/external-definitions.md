---
title: 外部定義
ms.date: 11/04/2016
helpviewer_keywords:
- external definitions
- external linkage, variable declarations
ms.assetid: 41e37bfc-b360-43b1-9972-28af2d365b20
ms.openlocfilehash: 98694abd0598ce1e601a7da74c4681442a71f7df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597648"
---
# <a name="external-definitions"></a>外部定義

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*external-declaration* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*external-declaration*: /\* 只能於外部 (檔案) 範圍內 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*function-definition*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*宣告*

*function-definition*: /\* 這裡的宣告子是函式宣告子 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *宣告子* *declaration-list*<sub>opt</sub> *compound-statement*

## <a name="see-also"></a>請參閱

[階段結構文法](../c-language/phrase-structure-grammar.md)