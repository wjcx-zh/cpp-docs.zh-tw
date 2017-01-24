---
title: "多執行緒的 Include 檔 | Microsoft Docs"
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
  - "Include 檔, 多執行緒"
  - "多執行緒 [C++], Include 檔"
  - "執行緒 [C++], Include 檔"
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多執行緒的 Include 檔
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

標準 Include 檔宣告 C 的執行階段程式庫函式，就好像它們是在程式庫裡實作一樣。  如果您使用[完全最佳化](../../build/reference/ox-full-optimization.md) \(\/Ox\) 或 [fastcall 呼叫慣例](../../build/reference/gd-gr-gv-gz-calling-convention.md) \(\/Gr\) 選項，編譯器會假設所有的函式都應該使用登錄呼叫慣例來呼叫。  Run\-Time 程式庫函式使用 C 的呼叫慣例來編譯，而且標準 Include 檔案中的宣告告訴編譯器要對這些函式產生正確的外部參考。  
  
## 請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../../parallel/multithreading-with-c-and-win32.md)