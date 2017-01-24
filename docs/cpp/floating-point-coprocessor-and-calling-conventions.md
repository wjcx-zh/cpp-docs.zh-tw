---
title: "浮點常數副處理器和呼叫慣例 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "浮點常數副處理器"
  - "浮點數"
  - "浮點數, 副處理器"
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 浮點常數副處理器和呼叫慣例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您要為浮點副處理器撰寫組件常式，除非您要傳回 **float** 或 **double** 值 \(其為函式應在 ST\(0\) 中傳回的值\)，否則必須保留浮點控制字詞並清除副處理器堆疊。  
  
## 請參閱  
 [呼叫慣例](../cpp/calling-conventions.md)