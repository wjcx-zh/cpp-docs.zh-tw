---
title: "MFC 資料庫文件 | Microsoft Docs"
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
  - "DAO [C++], MFC"
  - "資料庫 [C++], MFC"
  - "MFC [C++], 資料庫應用程式"
  - "ODBC [C++], MFC"
ms.assetid: bb120282-cd0d-4bf4-a27c-93b3501fb3a0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# MFC 資料庫文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

DAO 和 ODBC 類別的 MFC 文件是由下表列出的元件所組成：  
  
### MFC 資料庫文件  
  
|如需相關文件|請參閱|  
|------------|---------|  
|DAO 和 ODBC 的類別|《MFC 參考》中的類別名稱|  
|DAO 和 ODBC 的全域函式和巨集|《MFC 參考》中的函式或巨集名稱|  
|使用 MFC ODBC 類別進行程式設計|[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)|  
|DAO 和 ODBC 的技術提示 \(Technical Note\)|[MFC 技術提示](../mfc/technical-notes-by-category.md)|  
  
##  <a name="_core_mfc_documentation_and_dao_documentation"></a> MFC 文件和 DAO 文件  
 在整份 MFC DAO 類別的 MFC 文件中，您會在 DAO SDK 文件 \(包含於線上文件\) 中找到主題參考。  由於 MFC 將 DAO 封裝 \(或包裝\) 起來，所以 MFC 文件：  
  
-   焦點放在 MFC 上，以及它和底層 DAO 實作的不同之處。  
  
-   指引您至 DAO SDK 說明主題以取得底層的詳細資訊。  這些交互參考通常表示為「DAO 說明中的主題 *X*」。  
  
-   指出 MFC 與 DAO 執行方式的不同之處。  MFC 並沒有包裝所有的 DAO。  例如，MFC 並未提供 DAO 安全性功能的物件。  
  
> [!NOTE]
>  DAO SDK 說明是一個獨立的說明檔。  在此版本的 Visual C\+\+ 中，並沒有從該文件連結至 DAO 說明的超文字連結。  
  
> [!NOTE]
>  當瀏覽 DAO SDK 說明檔中的主題時，可能要進行部分轉譯。  在主要的 DAO SDK 文件中的範例是以 Basic 程式語言所撰寫的，而非 C\+\+ \(不過 DAO SDK 有提供一套不使用 MFC 的 C\+\+ 範例\)。  
  
##  <a name="_core_mfc_documentation_and_odbc_documentation"></a> MFC 文件和 ODBC 文件  
 MFC ODBC 類別的 MFC 文件其組織方式全然不同。  MFC ODBC 類別提供高層次的抽象，建立在 ODBC 之上，而不是在 ODBC API 的包裝上。  因此，此兩個文件集之間的連接比 MFC 和 DAO 文件集要來的少。  ODBC 文件使用比 Basic 更接近 C\+\+ 的 C 語言。  
  
## 請參閱  
 [MFC 資料庫類別 \(ODBC 和 DAO\)](../data/mfc-database-classes-odbc-and-dao.md)   
 [ODBC 的基本概念](../data/odbc/odbc-basics.md)