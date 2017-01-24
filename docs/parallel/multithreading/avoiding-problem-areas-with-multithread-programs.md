---
title: "避免具有多執行緒程式的問題區域 | Microsoft Docs"
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
  - "錯誤 [C++], 多執行緒程式"
  - "多執行緒 [C++], 疑難排解"
  - "執行緒 [C++], 疑難排解"
  - "疑難排解 [C++], 多執行緒"
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 避免具有多執行緒程式的問題區域
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在建立、連結或執行多執行緒 C 程式時，您會遇到許多問題。  下表中說明了某些更常見的問題 \(如需從 MFC 觀點出發的類似討論，請參閱[多執行緒：程式設計提示](../../parallel/multithreading-programming-tips.md)\)。  
  
|問題|可能原因|  
|--------|----------|  
|您得到一個訊息方塊，顯示您的程式造成保護違規。|許多 Win32 程式設計錯誤會造成保護違規。  常見造成保護違規的原因是將資料間接指派給 Null 指標。  因為這會造成您的程式嘗試存取不屬於它的記憶體，因此會發出保護違規。<br /><br /> 要偵測造成保護違規的原因有個簡單的方法，就是以偵錯資訊來編譯您的程式，然後經由 Visual C\+\+ 環境中的偵錯工具來執行。  當保護錯誤發生時，Windows 會將控制權轉移到偵錯工具，而且游標會停在造成問題的那一行上。|  
|您的程式產生許多編譯和連結錯誤。|您可以藉著將編譯器的警告層級設定為其最高值並留心警告訊息，減少許多可能的問題。  藉著使用層級 3 或層級 4 警告層級選項，您可以偵測不預期的資料轉換、遺漏的函式原型 \(Prototype\) 和非 ANSI 功能的使用。|  
  
## 請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../../parallel/multithreading-with-c-and-win32.md)