---
title: 運算錯誤 M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: 68e6ae823613d87eb01c443b564b46746259cd7b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173721"
---
# <a name="math-error-m6108"></a>運算錯誤 M6108

平方根

平方根運算中的運算元為負數。

程式終止，結束代碼為136。

> [!NOTE]
>  C 執行時間程式庫和 FORTRAN 內建函式**SQRT**中的 `sqrt` 函式不會產生此錯誤。 C `sqrt` 函式會先檢查引數，再執行作業，如果運算元為負數，則會傳回錯誤值。 FORTRAN **SQRT**函數會產生網域錯誤[M6201](../../error-messages/tool-errors/math-error-m6201.md) ，而不是這個錯誤。
