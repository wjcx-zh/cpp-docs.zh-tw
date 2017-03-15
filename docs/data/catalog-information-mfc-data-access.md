---
title: "目錄資訊 (MFC 資料存取) | Microsoft Docs"
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
  - "目錄資訊資料庫 [C++]"
  - "DAO [C++], 目錄資訊"
  - "資料庫 [C++], 目錄資訊資料庫"
  - "ODBC [C++], 目錄資訊"
  - "資料表 [C++]"
  - "資料表 [C++], 目錄資訊"
ms.assetid: c184e80f-ff17-409f-9df8-05275080bb8d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 目錄資訊 (MFC 資料存取)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

資料來源中的資料表可以納入資料表名稱及這些資料表中的資料行，還有資料表權限、主要與外部索引鍵名稱的相關資訊，以及預先定義的查詢或預存程序的相關資訊，以及資料表上的索引和資料表統計資料的相關資訊。  
  
 如需詳細資訊，請參閱[資料來源：決定資料來源的結構描述 \(ODBC\)](../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)。  
  
> [!NOTE]
>  在 MFC DAO 類別中，您可以取得如下的目錄資訊：使用 [CDaoDatabase::GetTableDefCount](../Topic/CDaoDatabase::GetTableDefCount.md) 和 [CDaoDatabase::GetTableDefInfo](../Topic/CDaoDatabase::GetTableDefInfo.md) 列舉資料庫中的資料表，並取得 [CDaoTableDefInfo](../mfc/reference/cdaotabledefinfo-structure.md) 結構中每個資料表的資訊。  
  
## 請參閱  
 [Data Access Programming \(MFC\/ATL\)](../data/data-access-programming-mfc-atl.md)