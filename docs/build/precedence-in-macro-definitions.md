---
title: "巨集定義的優先順序 | Microsoft Docs"
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
helpviewer_keywords: 
  - "巨集, 優先順序"
  - "NMAKE 程式, 巨集定義的優先順序"
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 巨集定義的優先順序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果巨集有多個定義，NMAKE 會使用最高優先順序的定義。  下列清單由最高到最低，顯示出優先的順序：  
  
1.  在命令列中定義的巨集  
  
2.  在 Makefile 或 Include 檔案中定義的巨集  
  
3.  繼承的環境變數巨集  
  
4.  在 Tools.ini 檔案中定義的巨集  
  
5.  預先定義的巨集，如 [CC](../build/command-macros-and-options-macros.md) 和 [AS](../build/command-macros-and-options-macros.md)  
  
 使用 \/E 導致繼承自環境變數的巨集覆寫有相同名稱的 Makefile 巨集。  使用 **\!UNDEF** 覆寫命令列。  
  
## 請參閱  
 [定義 NMAKE 巨集](../build/defining-an-nmake-macro.md)