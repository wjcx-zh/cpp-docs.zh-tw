---
title: "嚴重錯誤 C1900 | Microsoft Docs"
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
  - "C1900"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1900"
ms.assetid: 3aaa583b-4c1a-45de-aa34-527d806f2cb5
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 嚴重錯誤 C1900
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'Tool1' 版本 'number1' 與 'tool2' 版本 'number2' 之間的 Il 不符  
  
 在編譯器的不同階段中執行的工具不符。  ***number1*** 和 ***number2*** 指的是檔案上的日期。  例如，在階段 1，編譯器前端執行 \(c1.dll\)，而在階段 2 中，編譯器後端執行 \(c2.dll\)。  檔案上的日期必須相符。  
  
 若要修正這個問題，請確定所有的更新都已套用到 Visual Studio。  如果問題持續發生，請使用 Windows \[控制台\] 中的 \[程式和功能\] 來修復或重新安裝 Visual Studio。