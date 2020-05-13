---
title: 後置運算子
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: a86ede25feeaee3a9fb1c6b146cf9667b85c0c2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232243"
---
# <a name="postfix-operators"></a>後置運算子

後置運算子在運算式評估時具有最高優先順序 (具有更緊密的繫結)。

## <a name="syntax"></a>語法

後置*運算式*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;後置*運算式***[***運算式***]**      <br/>
&nbsp;&nbsp;&nbsp;&nbsp;後置*運算式***（***引數運算式清單*<sub>opt</sub> **）**    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;後置*運算式***。**    *識別碼 (identifier)*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*後置運算式*  **->**  *識別碼*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*後置運算式*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*後置運算式*  **--**

此優先順序層級的運算子為陣列註標、函式呼叫、結構和等位成員，以及後置遞增和遞減運算子。

## <a name="see-also"></a>請參閱

[C 運算子](../c-language/c-operators.md)
