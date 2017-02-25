---
title: "類型 double | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "double 資料類型"
  - "尾數, 浮點變數"
  - "可移植性 [C++], 類型 double"
  - "類型 double"
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 類型 double
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 double 類型的雙精確度值有 8 個位元組。  其格式類似於浮點格式，但是它有 11 位額外的 1023 指數和一個 52 位元尾數，再加上隱含的 1 個高序位位元。  若是 double 類型，此格式的範圍大約從 1.7E–308 到 1.7E\+308。  
  
 **Microsoft 特定的**  
  
 double 類型包含 64 個位元：1 表示正負號，11 表示指數，52 則表示尾數。  其範圍是 \+\/– 1.7E308，且具有至少 15 位數的整數位數。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [基本類型的儲存空間](../c-language/storage-of-basic-types.md)