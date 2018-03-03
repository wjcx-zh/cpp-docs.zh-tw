---
title: "MFC ODBC 消費者精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.class.mfc.consumer.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC ODBC Consumer Wizard
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad9e4aeb15d2af04987883b6554d569e3cc16b8d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-odbc-consumer-wizard"></a>MFC ODBC 消費者精靈
在這裡插入摘要的 「 搜尋結果 」。  
  
 這個精靈設定 ODBC 資料錄集類別和資料繫結存取指定的資料來源所需。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **資料來源**  
 **資料來源**按鈕可讓您指定的資料來源以使用指定的 ODBC 驅動程式設定。 如需有關資料來源檔案 (DSN) 的詳細資訊，請參閱[檔案資料來源](https://msdn.microsoft.com/library/ms715401.aspx)ODBC SDK 中。 **選取資料來源**對話方塊有兩個索引標籤：  
  
-   **檔案資料來源** 索引標籤：**查看**方塊會指定在其中選取要用做為資料來源檔案的目錄。 預設為 \Program Files\Common Files\ODBC\Data 來源。 現有的檔案資料來源 （.dsn 檔案） 會出現在主清單方塊中。 您可以預先時間使用的資料來源設定**檔案 DSN**索引標籤上[ODBC 資料來源管理員](https://msdn.microsoft.com/library/ms714024.aspx)，或建立新的使用此對話方塊。  
  
     若要建立新的檔案資料來源從這個對話方塊中，按一下`New`指定 DSN 名稱;**建立新的資料來源** 對話方塊隨即出現。 在**建立新的資料來源**對話方塊方塊中選取適當的驅動程式，然後按一下`Next`; 按一下**瀏覽**，然後選取要做為資料來源 （您必須選取 所有檔案 以檔案名稱檢視非 DSN 檔案，例如.xls 檔案）;按一下`Next`，然後按一下 **完成**。 （如果您選取的非 DSN 檔案時，您會取得特定驅動程式對話方塊中的，例如 ODBC Microsoft Excel < 安裝 >，這會將檔案轉換為 DSN）。  
  
    > [!NOTE]
    >  您也可以建立新的檔案資料來源，先使用 ODBC 資料來源管理員。 從**啟動**功能表上，選取**設定**，**控制台**，**系統管理工具**，**資料來源 (ODBC)**，然後**ODBC 資料來源管理員**。  
  
     **DSN 名稱**方塊可讓您指定的檔案資料來源的名稱。 您必須確定 DSN 名稱結尾副檔名為適當的檔案，例如 Excel 檔案的.xls 或.mdb 檔案的存取。  
  
     如需有關名稱 （dsn） 的詳細資訊，請參閱[檔案資料來源](https://msdn.microsoft.com/library/ms715401.aspx)ODBC SDK 中。  
  
-   **資料來源的機器** 索引標籤： 此索引標籤會列出系統和使用者資料來源。 使用者資料來源專屬於此機器上的使用者。 系統資料來源可供所有使用者在這部電腦上或全系統服務。 請參閱[機器資料來源](https://msdn.microsoft.com/library/ms710952.aspx)ODBC SDK 中  
  
 如需有關 ODBC 資料來源的詳細資訊，請參閱[資料來源](https://msdn.microsoft.com/library/ms711688.aspx)ODBC SDK 中。  
  
 按一下**確定**完成。 **選取資料庫物件** 對話方塊隨即出現。 從這個對話方塊中，選取資料表或檢視的取用者會使用。 請注意，您可以按住 control 鍵同時按一下的項目上選取多個檢視和資料表。  
  
 **類別**  
 取用者類別中，依預設是根據您選取的檔案或機器資料來源名稱的名稱。  
  
 **.h 檔案**  
 取用者類別標頭檔名稱，依預設是根據您選取檔案或電腦的資料來源的名稱。  
  
 **.cpp 檔案中**  
 取用者類別實作檔的名稱，依預設是根據您選取檔案或電腦的資料來源的名稱。  
  
 **Type**  
 指定資料錄集是否為動態集 （預設值） 或快照集。  
  
-   **動態集**： 指定資料錄集是動態集。 動態集是提供查詢的資料庫資料的索引檢視表查詢的結果。 動態集快取的整數索引原始資料，並因此提供了一效能中取得快照集。 索引會指向直接每一筆記錄找到為查詢的結果，並指出是否要清除記錄。 您也在查詢記錄的更新資訊的存取。 這是預設值。  
  
-   **快照集**： 指定資料錄集是快照集。 快照是查詢的結果，而且時間是在某個時間點的資料庫檢視。 快取查詢結果所發現的所有記錄，因此不會看到原始記錄的任何變更。  
  
 **繫結的所有資料行**  
 指定選取之資料表中的所有資料行是否繫結。 如果您選取此方塊 （預設值），都繫結的所有資料行;如果您未選取此方塊，沒有資料行繫結，以及您必須將其繫結以手動方式在資料錄集類別。  
  
## <a name="see-also"></a>請參閱  
 [MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)

