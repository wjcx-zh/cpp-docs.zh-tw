---
title: "嚴重錯誤 C1905 | Microsoft Docs"
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
  - "C1905"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1905"
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1905
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

前端和後端不相容 \(必須以相同處理器為目標\)  
  
 當 .obj 檔是由專門處理 x86、ARM 或 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 這類處理器的編譯器前端 \(C1.dll\) 產生，但卻由專門處理不同處理器的後端 \(C2.dll\) 讀取時，就會產生這項錯誤。  
  
 若要修正這個問題，請確定您使用相符的前端和後端。  這是在 Visual Studio 中所建立專案的預設值。  如果您有編輯專案檔，並使用編譯器工具的不同路徑，可能會發生這個錯誤。  如果您沒有特別設定編譯器工具的路徑，則如果您的 Visual Studio 安裝已損毀，就可能會發生這個錯誤。  比方說，您可能將編譯器 .dll 檔案由一個位置複製到另一個位置。  請使用 Windows \[控制台\] 中的 \[程式和功能\] 來修復或重新安裝 Visual Studio。