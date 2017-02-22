---
title: "ODBC：ODBC 資料指標程式庫 | Microsoft Docs"
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
  - "資料指標程式庫 [ODBC]"
  - "資料指標程式庫 [ODBC], 快照"
  - "游標, ODBC 資料指標程式庫"
  - "層級 1 ODBC 驅動程式"
  - "ODBC 資料指標程式庫 [ODBC]"
  - "ODBC 驅動程式, 資料指標支援"
  - "ODBC 驅動程式, 層級 1"
  - "ODBC, 時間戳記"
  - "定位更新"
  - "資料指標位置"
  - "快照, ODBC 中的支援"
  - "靜態資料指標"
  - "時間戳記, ODBC 時間戳記資料行"
ms.assetid: 6608db92-82b1-4164-bb08-78153c227be3
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ODBC：ODBC 資料指標程式庫
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題會說明 ODBC 資料指標程式庫以及如何使用它。  如需詳細資訊，請參閱：  
  
-   [資料指標程式庫和層級 1 ODBC 驅動程式](#_core_the_cursor_library_and_level_1_odbc_drivers)  
  
-   [定位更新和時間戳記資料行](#_core_positioned_updates_and_timestamp_columns)  
  
-   [使用資料指標程式庫](#_core_using_the_cursor_library)  
  
 ODBC 資料指標程式庫是位於 ODBC 驅動程式管理員和驅動程式之間的動態連結程式庫 \(DLL\)。  在 ODBC 方面，驅動程式會維持資料指標來追蹤在資料錄集中的位置。  資料指標會標記您在資料錄集中已捲動過的位置 ─ 即目前的資料錄。  
  
##  <a name="_core_the_cursor_library_and_level_1_odbc_drivers"></a> 資料指標程式庫和層級 1 ODBC 驅動程式  
 ODBC 資料指標程式庫將提供層級 1 驅動程式下述新功能：  
  
-   向前和向後捲動。  由於層級 2 驅動程式已經是可捲動，因此並不需要資料指標程式庫。  
  
-   快照集支援。  資料指標程式庫可以管理包含快照集資料錄的緩衝區。  這個緩衝區會反映程式對資料錄的刪除和編輯，但不會反映其他使用者的加入、刪除或編輯。  所以，快照集只會跟資料指標程式庫的緩衝區一樣新。  這個緩衝區只會在您呼叫 **Requery** 時反映您自己的加入情形。  動態集不會使用到資料指標程式庫。  
  
 資料指標程式庫會提供快照集 \(靜態資料指標\)，雖然您的驅動程式通常並不支援快照集。  如果驅動程式已經支援靜態資料指標，就不需要載入資料指標程式庫來取得快照集支援。  如果沒有使用資料指標程式庫，則只能使用快照集和順向 \(Forward\-only\) 的資料錄集。  如果驅動程式支援動態集 \(KEYSET\_DRIVEN 資料指標\) 而且想要望使用，則千萬不要使用該資料指標程式庫。  如果您希望同時使用快照集和動態集，那麼除非驅動程式可同時支援這兩種類型，否則必須將這兩種類型分別建立在不同的 `CDatabase` 物件上 \(兩種不同的連接\)。  
  
##  <a name="_core_positioned_updates_and_timestamp_columns"></a> 定位更新和時間戳記資料行  
  
> [!NOTE]
>  ODBC 資料來源可透過 MFC ODBC 類別存取 \(如本主題所述\)，或透過 MFC 資料存取物件 \(DAO\) 類別存取。  
  
> [!NOTE]
>  如果 ODBC 驅動程式支援 \(如果有，MFC 便會使用的\) **SQLSetPos**，則這個主題就不適用於您。  
  
 大多數的層級 1 驅動程式無法支援定位更新。  這種驅動程式會因這種因素，而使用資料指標程式庫來模擬層級 2 驅動程式的功能。  資料指標程式庫會在未變更欄位上製作一個已查詢的更新，以模擬定位更新支援。  
  
 在某些情況下，資料錄集可能會包含時間戳記資料行，做為其中一個未變更的欄位。  利用包含時間戳記資料行的資料表來使用 MFC 資料錄集時會產生兩個問題。  
  
 第一個問題與具有時間戳記資料行的資料表中的可更新快照集有關。  如果快照集所繫結的資料表包含了一個時間戳記資料行，就應該在呼叫 **Edit** 和 **Update** 之後呼叫 **Requery**。  如果沒有，您就可能無法再次編輯相同的資料錄。  當您呼叫 **Edit** 後又接著呼叫 **Update**，資料來源就會寫入該資料錄，而該時間戳記資料行也會完成更新。  如果您未呼叫 **Requery**，快照集資料錄的時間戳記值就不再符合在資料來源相對應的時間戳記。  當您嘗試再次更新該資料錄時，資料來源可能會因為不相符而不允許更新。  
  
 第二個問題則與使用 `RFX_Date` 函式傳輸時間、日期資訊到資料表或是取自資料表時 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 類別所產生的限制有關。  `CTime` 物件處理會在資料傳輸過程中使用其他中繼處理形式之配置方式。  `CTime` 物件的資料範圍對某些應用程式來說，也可能會產生相當大的限制。  `RFX_Date` 函式的新版本會接收一個 ODBC **TIMESTAMP\_STRUCT** 參數，而不是接收一個 `CTime` 物件。  如需詳細資訊，請參閱《MFC 參考》中[巨集和全域變數](../Topic/Macros,%20Global%20Functions,%20and%20Global%20Variables.md)的 `RFX_Date`。  
  
##  <a name="_core_using_the_cursor_library"></a> 使用資料指標程式庫  
 當您利用呼叫 [CDatabase::OpenEx](../Topic/CDatabase::OpenEx.md) 或 [CDatabase::Open](../Topic/CDatabase::Open.md) 連接到一個資料來源時，您可以指定該資料來源是否需要使用資料指標程式庫。  若您將要在該資料來源上建立快照集，請指定在 `OpenEx` 的 `dwOptions` 參數中的 **CDatabase::useCursorLib** 選項，或將 **Open** 的 **bUseCursorLib** 參數指定為 **TRUE** \(預設值為 **TRUE**\)。  若您的 ODBC 驅動程式支援動態集 \(Dynaset\)，且您希望在資料來源上開啟動態集，就千萬不要使用資料指標程式庫 \(其會遮罩某些動態集所需的驅動程式功能\)。  在那種情況下，請勿指定 `OpenEx` 的 **CDatabase::useCursorLib**，或是將 **Open**  的 **bUseCursorLib** 參數指定為 **FALSE**。  
  
## 請參閱  
 [ODBC 的基本概念](../../data/odbc/odbc-basics.md)