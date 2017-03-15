---
title: "C 執行階段錯誤 R6016 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6016"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6016"
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# C 執行階段錯誤 R6016
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行緒資料空間不足  
  
> [!NOTE]
>  如果您遇到這個錯誤訊息，表示具名程式因為發生內部記憶體問題已經關閉。  發生這個錯誤的原因可能有很多種，不過，通常是程式內的缺失或程式使用的 Visual C\+\+ 程式庫損毀所造成。  
>   
>  您可以嘗試進行下列步驟來修正這個錯誤：  
>   
>  -   使用 \[**控制台**\] 中的 \[**程式和功能**\] 頁面修復或重新安裝程式。  
> -   使用 \[**控制台**\] 中的 \[**程式和功能**\] 頁面修復或重新安裝 Microsoft Visual C\+\+ 可轉散發套件的所有複本。  
> -   在 \[**主控台**\] 中的 \[**Windows Update**\] 查看是否有軟體更新。  
> -   檢查是否有程式的更新版本。  
  
 發生這個錯誤，是因為程式未從作業系統收到足夠的記憶體來完成 [\_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) 或 `_beginthreadex` 呼叫，或是 `_beginthread` 或 `_beginthreadex` 尚未初始化執行緒區域儲存區。  
  
 當新的執行緒啟動時，程式庫必須為執行緒建立一個內部資料庫。  當使用作業系統提供的記憶體無法展開資料庫時，執行緒就無法啟動，呼叫的處理序也會停止。  當處理序已建立過多執行緒，或是執行緒區域儲存區已用盡時，就會發生這種情形。  
  
 我們建議，呼叫 C 執行階段程式庫 \(CRT\) 的可執行檔應該使用 `_beginthreadex` 建立執行緒，而不是使用 Window API `CreateThread`。  `_beginthreadex` 會初始化執行緒區域儲存區中許多 CRT 函式所使用的內部靜態儲存區。  如果您使用 `CreateThread` 建立執行緒，則呼叫需要已初始化的內部靜態儲存區的 CRT 函式時，CRT 可能會終止處理序並發出 R6016。