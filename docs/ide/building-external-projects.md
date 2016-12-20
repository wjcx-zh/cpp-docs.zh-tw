---
title: "建置外部專案 | Microsoft Docs"
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
  - "組建 [C++], 外部專案"
  - "外部專案"
  - "Makefile 專案, 外部專案"
  - "專案 [C++], 外部專案"
  - "Visual C++ 專案, 外部專案"
ms.assetid: 650b7803-ea91-489d-bee3-8f3e990e223c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 建置外部專案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

外部專案是一種使用 Makefile 或在 Visual C\+\+ 開發環境以外 \(外部\) 其他工具的 Visual C\+\+ 專案。  
  
 如果您有一個想要在 Visual C\+\+ 開發環境中建置的外部專案 \(例如 Makefile 專案\)，請在 Makefile 應用程式精靈中建立一個 Makefile 專案並且指定專案的建置命令和輸出。  如需詳細資訊，請參閱[建立 Makefile 專案](../ide/creating-a-makefile-project.md)。  
  
 請注意，Visual C\+\+ 已不再支援從開發環境匯出現用專案之 Makefile 的能力。  請使用 [Devenv 命令列參數](../Topic/Devenv%20Command%20Line%20Switches.md)從命令列建置 Visual Studio 專案。  
  
## 請參閱  
 [在 Visual Studio 中建置 C\+\+ 專案](../ide/building-cpp-projects-in-visual-studio.md)