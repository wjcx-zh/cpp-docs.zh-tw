---
title: 外部定義
ms.date: 11/04/2016
helpviewer_keywords:
- external definitions
- external linkage, variable declarations
ms.assetid: 41e37bfc-b360-43b1-9972-28af2d365b20
ms.openlocfilehash: 7a05cf730940246c82963afbe27f6fa344951aeb
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152348"
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

## <a name="see-also"></a>另請參閱

[階段結構文法](../c-language/phrase-structure-grammar.md)
