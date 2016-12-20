---
title: "浮點值反向溢位 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 浮點值反向溢位
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.5.1**：數學函式是否在反向溢位範圍錯誤上將整數運算式 `errno` 設定為巨集 `ERANGE` 的值  
  
 浮點反向溢位不會將運算式 `errno` 設為 `ERANGE`。  當值趨近於零，最終造成反向溢位時，會將其值設定為零。  
  
## 請參閱  
 [程式庫函式](../c-language/library-functions.md)