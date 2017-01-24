---
title: "我的標準 DLL 中有記憶體遺漏，但是我的程式碼看起來好好的。 我要如何發現記憶體遺漏？ | Microsoft Docs"
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
  - "DLL [C++], 記憶體遺漏"
  - "記憶體遺漏 [C++], DLL"
ms.assetid: a5d76573-b567-4b6a-8303-dafeeed9204d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 我的標準 DLL 中有記憶體遺漏，但是我的程式碼看起來好好的。 我要如何發現記憶體遺漏？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

造成記憶體遺漏 \(Memory Leak\) 的可能原因之一是 MFC 建立在訊息處理函式 \(Message Handler Function\) 內部使用的暫存物件。  在標準 DLL 裡，MFC 並不會自動釋放配置給這些物件的記憶體。  如需詳細資訊，請參閱[記憶體管理和偵錯堆積](http://msdn.microsoft.com/zh-tw/34dc6ef6-31c9-460e-a2a7-15e7f8e3334b)或知識庫文件＜Cleaning Up Temporary MFC Objects in \_USRDLL DLLs＞\(Q105286\)。  
  
 請注意，Visual C\+\+ 文件裡不再使用 USRDLL 詞彙。  靜態連結至 MFC 的標準 DLL 與之前的 USRDLL 有相同的特性。  知識庫文件裡的建議用法也適用於動態連結至 MFC 的標準 DLL。  上述知識庫文件裡的資訊適用於靜態連結至 MFC 的標準 DLL 和動態連結至 MFC 的標準 DLL。  
  
## 請參閱  
 [DLL 常見問題集](../build/dll-frequently-asked-questions.md)