---
title: "Microsoft 擴充功能 | Microsoft Docs"
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
  - "Microsoft 對 C/C++ 的擴充功能"
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Microsoft 擴充功能
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*asm\-statement*：  
 **\_\_asm**  *assembly\-instruction* **;** opt  
  
 **\_\_asm {**  *assembly\-instruction\-list*  **};** opt  
  
 *assembly\-instruction\-list*：  
 *assembly\-instruction* **;** opt  
  
 *assembly\-instruction* **;** *assembly\-instruction\-list* **;** opt  
  
 *ms\-modifier\-list*：  
 *ms\-modifier ms\-modifier\-list* opt  
  
 *ms\-modifier*：  
 **\_\_cdecl**  
  
 **\_\_fastcall**  
  
 **\_\_stdcall**  
  
 **\_\_syscall** \(保留供未來實作\)  
  
 **\_\_oldcall** \(保留供未來實作\)  
  
 **\_\_unaligned** \(保留供未來實作\)  
  
 *based\-modifier*  
  
 *based\-modifier*：  
 **\_\_based \(** *based\-type* **\)**  
  
 *based\-type*：  
 *name*  
  
## 請參閱  
 [文法摘要](../misc/grammar-summary-cpp.md)