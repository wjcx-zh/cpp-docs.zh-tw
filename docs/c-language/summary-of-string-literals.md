---
title: 字串常值的摘要 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: d2693900-f4e2-4820-b7de-085d51827aee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17f5f427efdcbdca6213989f6976fb734a74ba5c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092709"
---
# <a name="summary-of-string-literals"></a>字串常值的摘要

*string-literal*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**'** *s-char-sequence*<sub>opt</sub> **'**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**L'** *s-char-sequence*sub>opt</sub> **'**

*s-char-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*s-char-sequence* *s-char*

*s-char*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;原始程式碼字元集的任何成員，但雙引號 (")、反斜線 (\\) 或新行字元 escape-sequence 除外

## <a name="see-also"></a>請參閱

[語彙文法](../c-language/lexical-grammar.md)