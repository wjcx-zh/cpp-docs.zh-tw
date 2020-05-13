---
title: 運算錯誤 M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: c6bd403437ee5e55eaf4add288995d0e4aa76c3b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361964"
---
# <a name="math-error-m6108"></a>運算錯誤 M6108

平方根

平方根操作中的操作數為負數。

程序終止與退出代碼 136。

> [!NOTE]
> C`sqrt`執行時庫中的函數和 FORTRAN 內部函數**SQRT**不會生成此錯誤。 在執行操作`sqrt`之前,C 函數會檢查參數,如果操作數為負數,則返回錯誤值。 FORTRAN **SQRT**函數生成域錯誤[M6201](../../error-messages/tool-errors/math-error-m6201.md)而不是此錯誤。
