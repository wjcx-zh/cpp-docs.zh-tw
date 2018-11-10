---
title: 後置運算子
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: 45f7b67b62657c498bdd9ebcf5d85379cdcdd211
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440700"
---
# <a name="postfix-operators"></a>後置運算子

後置運算子在運算式評估時具有最高優先順序 (具有更緊密的繫結)。

## <a name="syntax"></a>語法

*postfix-expression*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **[**  *運算式*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-list*<sub>opt</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **.**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **->**  *識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **--**

此優先順序層級的運算子為陣列註標、函式呼叫、結構和等位成員，以及後置遞增和遞減運算子。

## <a name="see-also"></a>請參閱

[C 運算子](../c-language/c-operators.md)