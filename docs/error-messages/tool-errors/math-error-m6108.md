---
title: 運算錯誤 M6108 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6108
dev_langs:
- C++
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1624a89b472733b4adb5563c8ba52e0b03dcaa2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048613"
---
# <a name="math-error-m6108"></a>運算錯誤 M6108

平方根

平方根運算的運算元為負數。

程式結束，結束代碼第 136。

> [!NOTE]
>  `sqrt` C 執行階段程式庫和 FORTRAN 的內建函式中的函式**SQRT**不會產生此錯誤。 C`sqrt`函式前執行此作業會檢查引數，並傳回錯誤值，如果運算元為負數。 FORTRAN **SQRT**函式會產生網域錯誤[M6201](../../error-messages/tool-errors/math-error-m6201.md)而不是這個錯誤。