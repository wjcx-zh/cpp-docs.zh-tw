---
title: "MFC ODBC 消費者精靈 | Microsoft Docs"
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
  - "vc.codewiz.class.mfc.consumer.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ODBC 消費者精靈"
  - "精靈 [MFC]"
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
caps.latest.revision: 7
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ODBC 消費者精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在這裡插入「搜尋結果」摘要。  
  
 這個精靈會設定 ODBC 資料錄集類別以及存取特定資料來源所需的資料繫結。  
  
## UIElement 清單  
 **Data Source**  
 \[**資料來源**\] 按鈕讓您使用指定的 ODBC 驅動程式設定指定的資料來源。  如需關於資料來源檔案 \(資料來源名稱，DSN\) 的詳細資訊，請參閱《ODBC SDK》中的[檔案資料來源](https://msdn.microsoft.com/en-us/library/ms715401.aspx)。  \[**選取資料來源**\] 對話方塊有兩個索引標籤：  
  
-   \[**檔案資料來源**\] 索引標籤：\[查詢\] 方塊指定要在哪個目錄中選取當做資料來源的檔案。  預設值為 \\Program Files\\Common Files\\ODBC\\Data Sources。  現有檔案資料來源 \(.dsn 檔\) 會出現在主清單方塊中。  您可以先使用 [ODBC 資料來源管理員](https://msdn.microsoft.com/en-us/library/ms714024.aspx)的 \[**檔案型 DSN**\] 索引標籤設定資料來源，或是使用這個對話方塊建立新的資料來源。  
  
     若要從這個對話方塊來建立新的檔案資料來源，請按一下 \[`New`\] 來指定 DSN 名稱，\[建立新資料來源\] 對話方塊隨即出現。  在 \[建立新資料來源\] 對話方塊中選取適當驅動程式並按一下 \[`Next`\]；按一下 \[瀏覽\] 並選取要當做資料來源使用的檔案名稱 \(您必須選取 \[所有檔案\] 來檢視非 DSN 檔，例如 .xls 檔\)；按一下 \[`Next`\]，接著按一下 \[完成\] \(如果您選取非 DSN 檔，則會出現特定驅動程式的對話方塊，例如 \[ODBC Microsoft Excel 設定\]，將檔案轉換為 DSN\)。  
  
    > [!NOTE]
    >  您也可先使用 \[ODBC 資料來源管理員\] 建立新的檔案資料來源。  從 \[**開始**\] 功能表選取 \[**設定**\]、\[**控制台**\]、\[**系統管理工具**\]、\[資料來源 \(ODBC\)\]，然後選取 \[ODBC 資料來源管理員\]。  
  
     \[DSN 名稱\] 方塊允許您指定檔案資料來源的名稱。  您必須確定 DSN 名稱是以適當的副檔名結尾，例如 Excel 檔為 .xls 或 Access 檔為 .mdb。  
  
     如需 DSN 的詳細資訊，請參閱《ODBC SDK》中的[檔案資料來源](https://msdn.microsoft.com/en-us/library/ms715401.aspx)。  
  
-   \[機器資料來源\] 索引標籤：這個索引標籤會列出系統和使用者資料資源。  使用者資料來源是這個機器上的使用者特有的。  系統資料來源可讓這個機器上或是整個系統服務的所有使用者使用。  請參閱《ODBC SDK》中的[機器資料來源](https://msdn.microsoft.com/en-us/library/ms710952.aspx)。  
  
 如需 ODBC 資料來源的詳細資訊，請參閱《ODBC SDK》中的[資料來源](https://msdn.microsoft.com/en-us/library/ms711688.aspx)。  
  
 按一下 \[**確定**\] 完成。  \[選取資料庫物件\] 對話方塊隨即出現。  從這個對話方塊選取消費者將使用的資料表或檢視。  請注意，您可以按住控制鍵並按一下項目來選取多個檢視和資料表。  
  
 **類別**  
 消費者類別的名稱，預設為根據您選取之檔案或機器資料來源的名稱。  
  
 **.h 檔案**  
 消費者類別標頭檔 \(Header File\) 的名稱，預設為根據您選取之檔案或機器資料來源的名稱。  
  
 **.cpp 檔**  
 消費者類別實作檔 \(Implementation File\) 的名稱，預設為根據您選取之檔案或機器資料來源的名稱。  
  
 **型別**  
 指定資料錄集為動態集 \(Dynaset\) \(預設\) 或快照集 \(Snapshot\)。  
  
-   \[**動態集**\]：指定資料錄集是動態集。  動態集是查詢的結果，提供查詢資料庫資料的索引檢視表。  動態集只快取原始資料的整數索引，因此在效能上比快照集有利。  索引會直接指向查詢結果找到的每個資料錄，並指出資料錄是否已移除，  您也可存取查詢資料錄中的更新資訊。  這是預設值。  
  
-   \[**快照集**\]：指定資料錄集是快照集。  快照集是查詢的結果，提供在某個時間點上資料庫的檢視表。  查詢結果找到的所有資料錄都是快取的，因此您不會看到原始資料錄的任何變更。  
  
 **繫結所有資料行**  
 指定是否要繫結選取資料表中的所有資料行。  如果您選取這個方塊 \(預設\)，則會繫結所有資料行；如果您不選取這個方塊，則不會繫結任何資料行，而您必須在資料錄集類別中進行手動繫結。  
  
## 請參閱  
 [MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)