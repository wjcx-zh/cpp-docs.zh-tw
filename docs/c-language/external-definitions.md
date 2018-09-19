---
title: 外部定義 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- external definitions
- external linkage, variable declarations
ms.assetid: 41e37bfc-b360-43b1-9972-28af2d365b20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba0487716a24e75ec2fccfa9dc7803bff9a5cfcf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098845"
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