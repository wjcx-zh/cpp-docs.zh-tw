---
title: "資料錄集：執行聯結 (ODBC) | Microsoft Docs"
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
  - "資料繫結 [C++], 資料錄集中的資料行"
  - "資料繫結 [C++], 資料錄集資料行"
  - "篩選條件 [C++], 資料錄集的聯結條件"
  - "聯結 [C++], 在資料錄集中"
  - "ODBC 資料錄集 [C++], 聯結"
  - "資料錄集 [C++], 資料繫結"
  - "資料錄集 [C++], 聯結資料表"
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：執行聯結 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
## 什麼是聯結  
 聯結 \(Join\) 作業是一種常見的資料存取工作，讓您能以單一資料錄集物件來使用一個或更多個資料表的資料錄。  聯結兩個或更多的資料表會產生一個可以包含每個資料表資料行的資料錄集，而在您的應用程式只會看到一份單一資料表。  有時聯結會使用所有資料表內的所有資料行，而有時聯結內的 SQL **SELECT** 子句只使用每個資料表中的某些資料行。  資料錄類別支援唯讀聯結，而不支援可更新的聯結。  
  
 若要從聯結資料表中選取包含資料行的資料錄，您需要取得下列項目：  
  
-   一個包含所有聯結的資料表名稱之資料表清單。  
  
-   一個包含所有參與資料行名稱的資料行清單。  比對資料表名稱，取得名稱相同但位於不同資料表內的資料行。  
  
-   用以指定聯結的資料表中資料行之篩選條件 \(SQL **WHERE** 子句\)。  這個篩選條件形式為 Table1.KeyCol \= Table2.KeyCol，並實際地完成聯結。  
  
 您也可以將多對資料行納入方程式 \(每個配對會以 SQL 關鍵字 **AND** 聯結\)，使用相同方法來聯結兩個以上的資料表。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：宣告預先定義查詢的類別 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)   
 [資料錄集：宣告資料表的類別 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [資料錄集：重新查詢資料錄集 \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)