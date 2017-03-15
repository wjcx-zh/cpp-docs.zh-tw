---
title: "資料來源：以程式設計方式建立 ODBC 資料來源資料表 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ODBC 資料來源, 建立資料表"
  - "以程式設計方式建立 ODBC 資料表 [C++]"
  - "資料表 [C++]"
  - "資料表 [C++], 以程式設計方式建立"
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 資料來源：以程式設計方式建立 ODBC 資料來源資料表
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題說明如何使用 `CDatabase` 類別的 `ExecuteSQL` 成員函式，將包含 **CREATE TABLE** SQL 陳述式的字串傳遞至該函式，以便建立資料來源資料表。  
  
 如需 MFC 的 ODBC 資料來源的詳細資訊，請參閱[資料來源 \(ODBC\)](../../data/odbc/data-source-odbc.md)。  主題[資料來源：以程式設計方式設定 ODBC 資料來源](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md)會說明建立資料來源的詳細資訊。  
  
 當您建立了資料來源以後，就可以輕鬆地使用 `ExecuteSQL` 成員函式和 **CREATE TABLE** SQL 陳述式來建立資料表。  例如，若您擁有一個稱為 `myDB` 的 `CDatabase` 物件，您就可以使用下列 MFC 程式碼建立一份資料表：  
  
```  
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",   
                         OfficeName TEXT(10))");  
```  
  
 這個程式碼範例會在由 `myDB` 所維持的 Microsoft Access 資料來源連接中，建立名為 "OFFICES" 的資料表，這個資料表包含兩個欄位，"OfficeID" 和 "OfficeName"。  
  
> [!NOTE]
>  指定於 **CREATE TABLE** SQL 陳述式中的欄位型別 \(Field Type\)，可能會根據使用的 ODBC 驅動程式而有所不同。  Microsoft Query 程式 \(隨附於 Visual C\+\+ 1.5\) 是一個瞭解何種欄位型態可用於何種資料來源的方式。  在 Microsoft Query 中按一下 \[檔案\]，再按一下 \[Table\_Definition\]，然後選取資料來源的資料表，並查看顯示在 \[**類型**\] 下拉式方塊中的類型。  SQL 語法也可用來建立索引。  
  
## 請參閱  
 [資料來源 \(ODBC\)](../../data/odbc/data-source-odbc.md)