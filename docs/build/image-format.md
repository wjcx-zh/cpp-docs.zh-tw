---
title: "映像格式 | Microsoft Docs"
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
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 映像格式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可執行檔映像格式為 PE32\+。  可執行檔映像 \(DLL 和 EXE\) 的大小上限為 2 GB，因此可以使用具有 32 位元替代 \(Displacement\) 的相對定址 \(Addressing\) 來定址靜態映像資料。  這個資料包括了匯入位址表格、字串常數和靜態全域資料等等。  
  
## 請參閱  
 [x64 軟體慣例](../build/x64-software-conventions.md)