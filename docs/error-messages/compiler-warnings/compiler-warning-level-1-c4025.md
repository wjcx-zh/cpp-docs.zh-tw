---
title: "編譯器警告 (層級 1) C4025 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4025"
ms.assetid: c4f6a651-0641-4446-973e-8290065e49ad
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'number': 基底指標傳遞至擁有變數引數的函式: 參數號碼  
  
 將基底指標傳遞至具有變數引數的函式會導致指標正規化，但結果無法預期。 請不要將基底指標傳遞至具有變數引數的函式。