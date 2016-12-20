---
title: "編譯器警告 (層級 1) C4819 | Microsoft Docs"
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
  - "C4819"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4819"
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4819
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檔案包含無法在目前字碼頁 \(數字\) 中表示的字元。請以 Unicode 格式儲存檔案，以防止資料遺失。  
  
 在字碼頁無法表示檔案中所有字元的系統上編譯 ANSI 原始程式檔時，就會發生 C4819。  
  
 若要解決 C4819，請以 Unicode 格式儲存檔案。  在 Visual Studio 中，依序選擇 \[檔案\]、\[進階儲存選項\]。  在 \[進階儲存選項\] 對話方塊方塊中，選取可以表示檔案中所有字元的編碼方式 \(例如 UTF\-8\)，然後選擇 \[確定\]。