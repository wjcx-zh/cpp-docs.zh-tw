---
title: "資料錄集：書籤和絕對位置 (ODBC) | Microsoft Docs"
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
  - "SetAbsolutePosition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "絕對位置, ODBC 資料錄集"
  - "書籤"
  - "書籤, CDBVariant"
  - "書籤, ODBC 資料錄集"
  - "CDBVariant 類別, 書籤"
  - "資料指標 [ODBC], 資料錄集中的絕對位置"
  - "GetBookmark 方法"
  - "ODBC 資料錄集, 絕對位置"
  - "ODBC 資料錄集, 書籤"
  - "定位資料錄"
  - "資料錄定位"
  - "資料錄集, 絕對位置"
  - "資料錄集, 書籤"
  - "SetAbsolutePosition 方法"
  - "SetAbsolutePosition 方法, 書籤"
  - "SetBookmark 方法"
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料錄集：書籤和絕對位置 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 巡覽資料錄集時，您通常需要一個返回特定資料錄的方法。  資料錄的書籤和絕對位置提供兩個這樣的方法。  
  
 這個主題說明：  
  
-   [書籤的使用方式](#_core_bookmarks_in_mfc_odbc)。  
  
-   [使用絕對位置來設定目前資料錄的方式](#_core_absolute_positions_in_mfc_odbc)。  
  
##  <a name="_core_bookmarks_in_mfc_odbc"></a> MFC ODBC 內的書籤  
 書籤可唯一識別某個資料錄。  當您在資料錄集內巡覽時，無法永遠依賴資料錄的絕對位置，因為資料錄有可能已從資料錄集刪除。  最可信賴的儲存資料錄位置方法是使用它的書籤。  `CRecordset` 類別提供的成員函式，可以：  
  
-   取得目前資料錄的書籤，以便可將它儲存在變數中 [GetBookmark](../Topic/CRecordset::GetBookmark.md)。  
  
-   指定您先前儲存在變數 \([SetBookmark](../Topic/CRecordset::SetBookmark.md)\) 內的資料錄書籤，快速地移動到該資料錄。  
  
 下列範例示範了如何使用這些成員函式來標記目前資料錄，並於稍後返回：  
  
```  
// rs is a CRecordset or  
// CRecordset-derived object  
  
CDBVariant varRecordToReturnTo;  
rs.GetBookmark( varRecordToReturnTo );  
  
// More code in which you  
// move to other records  
  
rs.SetBookmark( varRecordToReturnTo );  
```  
  
 您不需要從 [CDBVariant Class](../../mfc/reference/cdbvariant-class.md)物件擷取基礎資料型別。  使用 `GetBookmark` 以設定書籤值，並使用 `SetBookmark` 以返回該書籤。  
  
> [!NOTE]
>  根據您的 ODBC 驅動程式和資料錄集類型而定，可能並未支援書籤。  您可輕易藉由呼叫 [CRecordset::CanBookmark](../Topic/CRecordset::CanBookmark.md) 來決定是否有支援書籤。  此外，若有支援書籤，您必須指定 [CRecordset::Open](../Topic/CRecordset::Open.md) 成員函式內的 **CRecordset::useBookmarks** 選項來明確地選擇實作書籤。  您也應該在特定資料錄集作業之後檢查書籤的保存性 \(Persistence\)。  例如，若您 **Requery** 資料錄集，書籤可能不再有效。  請呼叫 [CDatabase::GetBookmarkPersistence](../Topic/CDatabase::GetBookmarkPersistence.md) 以確認您是否能安全呼叫 `SetBookmark`。  
  
##  <a name="_core_absolute_positions_in_mfc_odbc"></a> MFC ODBC 的絕對位置  
 除了書籤，`CRecordset` 類別還可讓您指定序號位置來設定目前資料錄。  這可稱為絕對位置。  
  
> [!NOTE]
>  在順向資料錄集中無法使用絕對位置。  如需順向資料錄集的詳細資訊，請參閱[資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)。  
  
 若要使用絕對位置移動目前的資料錄指標，請呼叫 [CRecordset::SetAbsolutePosition](../Topic/CRecordset::SetAbsolutePosition.md)。  當您將一個值傳至 `SetAbsolutePosition` 時，相對於序號位置的資料錄會變成目前資料錄。  
  
> [!NOTE]
>  資料錄的絕對位置具有潛在的不可信賴性。  如果使用者刪除資料錄集的資料錄，則任何後續資料錄的序號位置都會改變。  建議您在移動目前資料錄時使用書籤方法。  如需詳細資訊，請參閱 [MFC ODBC 的書籤](#_core_bookmarks_in_mfc_odbc)。  
  
 如需資料錄集巡覽的詳細資訊，請參閱[資料錄集：捲動 \(ODBC\)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)