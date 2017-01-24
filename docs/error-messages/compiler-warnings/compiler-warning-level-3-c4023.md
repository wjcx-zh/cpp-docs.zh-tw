---
title: "編譯器警告 (層級 3) C4023 | Microsoft Docs"
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
  - "C4023"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4023"
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4023
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol' : 基底指標傳送至沒有原型的函式 : 參數號碼  
  
 將基底指標傳送至沒有原型的函式會導致指標正規化，但結果無法預期。  
  
 如果您針對要傳送的基底指標使用原型函式，則可以修正這個警告。