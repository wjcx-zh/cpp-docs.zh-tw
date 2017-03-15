---
title: "ODBC 管理員 | Microsoft Docs"
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
  - "ODBC 系統管理員"
  - "ODBC 中的系統管理員"
  - "驅動程式 [C++], ODBC"
  - "安裝 ODBC"
  - "ODBC [C++], ODBC 管理員"
  - "ODBC 管理員 [C++]"
  - "ODBC 資料來源 [C++], ODBC 管理員"
  - "ODBC 驅動程式 [C++], 安裝"
ms.assetid: b8652790-3437-4e7d-bc83-6ea6981f008b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ODBC 管理員
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ODBC 管理員可為您登錄和設定可用的本機或是跨網路間的[資料來源](../../data/odbc/data-source-odbc.md)。  精靈將會使用 ODBC 管理員所提供的資訊，來建立將您的使用者連接到資料來源的應用程式程式碼。  
  
 若要設定一個供 MFC ODBC 類別或 MFC 資料存取 \(DAO\) 類別使用的 ODBC 資料來源，您必須先登錄和設定該資料來源。  使用 ODBC 管理員來加入或移除資料來源。  您也可以根據 ODBC 驅動程式建立新的資料來源。  
  
 ODBC 管理員會在安裝過程中進行安裝。  如果選擇了 \[自訂安裝\]，且未在 \[資料庫選項\] 對話方塊中選取任何 ODBC 驅動程式，就必須再次執行 \[安裝\] 來安裝必要檔案。  
  
 在 \[安裝\] 過程中可以選取想要安裝的 ODBC 驅動程式。  您可以稍後使用 Visual C\+\+ 安裝程式來安裝其他隨附於 Visual C\+\+ 的驅動程式。  
  
 如果想要安裝未隨附於 Visual C\+\+ 的 ODBC 驅動程式，請執行該驅動程式隨附的安裝程式。  
  
#### 若要安裝隨附於 Visual C\+\+ 的 ODBC 驅動程式  
  
1.  執行 Visual C\+\+ 發佈 CD 的 \[安裝\]。  
  
     在安裝程式中隨即顯示開啟的對話方塊。  
  
2.  在每個對話方塊中按一下 \[下一步\]，直到您到達 \[安裝選項\] 對話方塊。  選取 \[自訂\]，然後按一下 \[`Next`\]。  
  
3.  清除在 \[Microsoft Visual C\+\+ 安裝程式\] 對話方塊中除了 \[資料庫選項\] 以外的所有核取方塊，然後按一下 \[詳細資料\] 以顯示 \[資料庫選項\] 對話方塊。  
  
4.  清除 \[Microsoft 資料存取物件\] 核取方塊，選取 \[Microsoft ODBC 驅動程式\] 選取方塊，然後再按一下 \[詳細資訊\]。  
  
     \[Microsoft ODBC 驅動程式\] 對話方塊隨即出現。  
  
5.  選取您希望安裝的驅動程式，再接著按兩次 \[確定\]。  
  
6.  按一下其餘對話方塊中的 \[下一步\]，開始安裝作業。  安裝程式會告知您安裝已經完成。  
  
 在安裝驅動程式後，您就可以使用 \[ODBC 管理員\] 設定資料來源。  您可以在「控制台」中找到 ODBC 圖示。  
  
## 請參閱  
 [開放式資料庫連接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [資料來源 \(ODBC\)](../../data/odbc/data-source-odbc.md)