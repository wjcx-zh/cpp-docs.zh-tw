---
title: 運算錯誤 M6108 |Microsoft 文件
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
ms.openlocfilehash: 4dfeca48aa04ebfbc097649e5c25253166c50dad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325847"
---
# <a name="math-error-m6108"></a>運算錯誤 M6108
平方根  
  
 平方根運算的運算元為負數。  
  
 程式終止，結束代碼 136。  
  
> [!NOTE]
>  `sqrt` C 執行階段程式庫和 FORTRAN 內建函式中的函式**SQRT**並不會產生這個錯誤。 C`sqrt`函式執行運算之前檢查引數，並傳回錯誤值，如果運算元為負數。 FORTRAN **SQRT**函式會產生網域錯誤[M6201](../../error-messages/tool-errors/math-error-m6201.md)而不是這個錯誤。