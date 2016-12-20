---
title: "1. Introduction | Microsoft Docs"
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
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 1. Introduction
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這份文件中指定編譯器指示詞、 程式庫函式，以及可用來指定在 c 和 C\+\+ 程式中的共用記憶體的平行處理原則的環境變數的集合。  這份文件中描述的功能統稱為 *OpenMP C\/C\+\+ 應用程式介面 \(API\)*。  這項規格的目標是提供平行程式設計模型，能讓程式跨不同廠商的共用記憶體架構可攜性。  OpenMP C\/C\+\+ API 將支援許多廠商的編譯器。  有關 OpenMP，包括 *OpenMP Fortran 應用程式介面*，請參閱下列網站：  
  
 [http:\/\/www.openmp.org](http://www.openmp.org)  
  
 指示詞、 程式庫函式和這份文件中所定義的環境變數，可讓使用者建立及管理平行處理程式，同時允許可攜性。  指示詞擴充 c 和 C\+\+ 循序程式設計模型與單一程式多個資料 \(SPMD\) 建構、 工作共用的結構和同步處理建構，並提供支援的 「 共用 」 和 「 私有化 」 的資料。  編譯器支援 OpenMP C 和 C\+\+ API 將包含命令列選項，編譯器會啟動，並允許所有 OpenMP 編譯器指示詞的解譯。