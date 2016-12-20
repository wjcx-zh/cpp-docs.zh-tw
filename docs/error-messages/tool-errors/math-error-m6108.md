---
title: "運算錯誤 M6108 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "M6108"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6108"
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 運算錯誤 M6108
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

平方根  
  
 平方根作業中的運算元為負數。  
  
 程式以結束代碼 136 結束。  
  
> [!NOTE]
>  C 執行階段程式庫中的 `sqrt` 函式和 FORTRAN 的內建函式 **SQRT** 並不會產生此錯誤。  C `sqrt` 函式會在執行運算前檢查引數，當運算元為負數時傳回錯誤值。  FORTRAN **SQRT** 函式會產生 DOMAIN 錯誤 [M6201](../../error-messages/tool-errors/math-error-m6201.md)，而不是這個錯誤。