---
title: "Compiler Error C3550 | Microsoft Docs"
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
  - "C3550"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3550"
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C3550
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此內容中不得有純 'decltype\(auto\)'  
  
 如果 `decltype(auto)` 做為函式傳回類型的預留位置，則必須由本身使用。  它不能在指標宣告 \(`decltype(auto*)`\)、參考宣告 \(`decltype(auto&)`\) 或任何其他這類限定性條件中使用。  
  
## 請參閱  
 [auto](../../cpp/auto-cpp.md)