---
title: "符合 ANSI C 標準 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Ansi"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ANSI [C++], C 標準"
  - "相容性 [C++], ANSI C"
  - "符合 ANSI C 標準"
  - "慣例 [C++], Microsoft 的擴充功能"
  - "Microsoft 擴充功能命名慣例"
  - "命名慣例 [C++], Microsoft 程式庫"
  - "底線"
  - "底線, 前置"
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 符合 ANSI C 標準
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

所有 Microsoft 特定識別項的命名慣例在這個執行階段系統 \(例如函式、巨集、常數、變數和型別定義\) 是 ANSI 標準。  本文件，按照 ANSI\/ISO C 標準的所有執行階段函式被注意為 ANSI 相容。  ANSI 相容的應用程式只能使用這些 ANSI 相容函式。  
  
 Microsoft 特定函式和全域變數名稱從單一底線為開頭。  在您的程式碼範圍內，這些名稱只能在本機覆寫。  例如，當您包含 Microsoft 執行階段標頭檔時，您仍然可以宣告具有相同名稱的區域變數會覆寫 Microsoft 特定功能的 `_open` 。  不過，您無法針對全域函式或全域變數使用這個名稱。  
  
 Microsoft 專有的巨集和資訊清單常數名稱開始從兩個底線，或者以大寫字母後面會加上一個前置底線。  範圍這些識別項是絕對的。  例如，您無法使用此使用 Microsoft 特定識別項 **\_UPPER** 。  
  
## 請參閱  
 [相容性](../c-runtime-library/compatibility.md)