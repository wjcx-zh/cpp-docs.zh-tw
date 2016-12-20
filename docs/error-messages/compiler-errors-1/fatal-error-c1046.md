---
title: "嚴重錯誤 C1046 | Microsoft Docs"
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
  - "C1046"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1046"
ms.assetid: 822ec5f5-b0b0-4711-99e1-fc237b619af6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1046
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

編譯器限制：巢狀結構太深  
  
 結構、等位或類別 \(Class\) 超過巢狀限制，最高是 15 層。  請重新撰寫定義來減少巢狀層級。  透過使用 `typedef`  定義一個或多個巢狀結構，將結構、等位或類別分割成兩個或多個部分。