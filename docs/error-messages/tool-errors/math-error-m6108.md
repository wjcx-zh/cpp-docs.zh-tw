---
title: "運算錯誤 M6108 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6108
dev_langs: C++
helpviewer_keywords: M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c6db123d9cb96274848a3edd9f845f86f413d8e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6108"></a>運算錯誤 M6108
平方根  
  
 平方根運算的運算元為負數。  
  
 程式終止，結束代碼 136。  
  
> [!NOTE]
>  `sqrt` C 執行階段程式庫和 FORTRAN 內建函式中的函式**SQRT**並不會產生這個錯誤。 C`sqrt`函式執行運算之前檢查引數，並傳回錯誤值，如果運算元為負數。 FORTRAN **SQRT**函式會產生網域錯誤[M6201](../../error-messages/tool-errors/math-error-m6201.md)而不是這個錯誤。