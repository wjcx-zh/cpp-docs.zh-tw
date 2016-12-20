---
title: "ODBC 和資料庫類別 | Microsoft Docs"
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
  - "資料庫類別 [C++], ODBC"
  - "MFC [C++], ODBC 和"
  - "ODBC API 函式 [C++]"
  - "ODBC 類別 [C++], MFC 資料庫類別"
ms.assetid: b166f82d-6f85-4556-aac8-fb851235d22c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ODBC 和資料庫類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MFC ODBC 資料庫類別可以封裝通常您會自行在 [CDatabase](../../mfc/reference/cdatabase-class.md) 和 [CRecordset](../../mfc/reference/crecordset-class.md) 類別的成員函式中製作的 ODBC API 函式呼叫。  例如，複雜 ODBC 呼叫順序，將傳回資料錄繫結至儲存體位置、錯誤情況處理和由資料庫類別管理的其他作業。  如此一來，您就可以使用一個相當簡單的類別介面，來透過資料錄集物件實作資料錄。  
  
> [!NOTE]
>  ODBC 資料來源可透過 MFC ODBC 類別存取 \(如本主題所述\)，或透過 MFC 資料存取物件 \(DAO\) 類別存取。  
  
 儘管資料庫類別可以封裝 ODBC 功能，但他們並未提供 ODBC API 函式的一對一對應 \(One\-To\-One Map\)。  資料庫類別提供了一個在 Microsoft Access 和 Microsoft Visual Basic 尋找到資料存取物件後完成模式化的更高層級的抽象層。  如需詳細資訊，請參閱 [MFC 資料庫程式撰寫模型是什麼？](../../data/what-is-the-mfc-database-programming-model-q.md)。  
  
## 請參閱  
 [ODBC 的基本概念](../../data/odbc/odbc-basics.md)