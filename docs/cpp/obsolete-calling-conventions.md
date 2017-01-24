---
title: "過時呼叫慣例 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__fortran"
  - "__pascal"
  - "__syscall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__fortran 關鍵字 [C++]"
  - "__pascal 關鍵字 [C++]"
  - "__syscall 關鍵字 [C++]"
  - "呼叫慣例, 過時"
  - "WINAPI"
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 過時呼叫慣例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 不再支援 **\_\_pascal**、**\_\_fortran** 和 **\_\_syscall** 呼叫慣例。  您可以使用其中一種支援的呼叫慣例和適當的連結器選項模擬其功能。  
  
 WINDOWS.H 現在支援 **WINAPI** 巨集，它會轉譯為適合目標的呼叫慣例。  請在先前使用 **PASCAL** 和 **\_\_far \_\_pascal** 的位置使用 **WINAPI**。  
  
## END Microsoft 特定的  
  
## 請參閱  
 [引數傳遞和命名慣例](../cpp/argument-passing-and-naming-conventions.md)