---
title: "使用預存程序 | Microsoft Docs"
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
  - "OLE DB 提供者樣板, 預存程序"
  - "OLE DB, 預存程序"
  - "預存程序, 關於預存程序"
  - "預存程序, OLE DB"
  - "預存程序, Visual C++"
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用預存程序
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

預存程序 \(Stored Procedure\) 是一種儲存在資料庫中的可執行物件。  呼叫一個預存程序類似於叫用一個 SQL 命令。  在資料來源上使用預存程序 \(而不是在用戶端應用程式執行或準備陳述式\) 可提供數個優點，包括：提高效能、減少網路負擔，以及改善一致性和準確性。  
  
 預存程序可以具有任何數目 \(包括零\) 的輸入或輸出參數，而且可以傳遞傳回值。  您可以將參數值硬式編碼成特定資料值，或使用參數標記 \(問號 '?'\)。  
  
> [!NOTE]
>  使用 Visual C\+\+ 所建立的 CLR SQL Server 預存程序在編譯時必須使用 **\/clr:safe** 編譯器選項。  
  
 OLE DB Provider for SQL Server \(SQLOLEDB\) 可以支援下列預存程序用來傳回資料的機制：  
  
-   程序中的每個 SELECT 陳述式都會產生一個結果集 \(Result Set\)。  
  
-   程序可以透過輸出參數傳回資料。  
  
-   程序可以有一個整數的傳回碼 \(Return Code\)。  
  
> [!NOTE]
>  您不能將預存程序與 OLE DB Provider for Jet 一起使用，因為該提供者並不支援預存程序，查詢字串中只能使用常數。  
  
## 請參閱  
 [使用 OLE DB 消費者樣板](../../data/oledb/working-with-ole-db-consumer-templates.md)