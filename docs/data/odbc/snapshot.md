---
title: "快照集 | Microsoft Docs"
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
  - "資料指標程式庫 [ODBC], 快照"
  - "資料指標 [ODBC], static"
  - "ODBC 資料指標程式庫 [ODBC], 快照"
  - "ODBC 資料錄集, 快照"
  - "資料錄集, 快照"
  - "快照"
  - "快照, ODBC 中的支援"
  - "靜態資料指標"
ms.assetid: b5293a52-0657-43e9-bd71-fe3785b21c7e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 快照集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

快照集 \(Snapshot\) 是指一個可以反映在建立該快照集時所存在的資料之靜態檢視的資料錄集。  當您開啟了快照集並移動至所有資料錄時，它所包含的資料錄集和資料錄的值在您呼叫 **Requery** 重建快照集之前，都不會有所變更。  
  
> [!NOTE]
>  本文件適用於 MFC ODBC 類別。  若您正在使用 MFC DAO 類別，而非使用 MFC ODBC 類別，請參閱 [CDaoRecordset::Open](../Topic/CDaoRecordset::Open.md) 取得快照集類型資料錄集的詳細資訊。  
  
 您可以使用資料庫類別建立可更新的或是唯讀的快照集。  可更新的快照集與動態集不同，它不會反映其他使用者所做的資料錄值變更，但會反映您的程式所做的更新和刪除。  快照集中所加入的資料錄在您呼叫 **Requery**  之前是不可見的。  
  
> [!TIP]
>  快照集是 ODBC 靜態資料指標。  靜態資料指標實際上要等到您捲動到某資料錄之前，才會取得該資料列的資料。  若要確保即時擷取所有資料錄，您可以捲動至資料錄集終點，然後再捲動到想要查看的第一筆資料錄。  儘管如此，請您注意捲動到終點會需要額外配置，並會降低效能。  
  
 在您需要資料來維持固定的作業過程 \(例如，產生一份報表或執行運算\) 時，快照集會特別有用。  即使如此，資料來源與您的快照集仍具有相當大的差異，所以您可能會想要逐次地進行重建。  
  
 快照集支援是 ODBC 資料指標程式庫架構，可提供靜態資料指標和定位更新 \(可更新性所需\) 給任何層級 1 驅動程式。  資料指標程式庫 DLL 必須載入記憶體中才可獲得此項支援。  您必須在建構 `CDatabase` 物件和呼叫其 `OpenEx` 成員函式時，指定 `dwOptions` 參數的 **CDatabase::useCursorLib** 選項。  若您呼叫了 **Open** 成員函式，資料指標程式庫就會依預設載入。  如果您是使用動態集而非快照集，您就不會想要載入資料指標程式庫。  
  
 只有在建構 `CDatabase` 物件時載入 ODBC 資料指標程式庫，或是您正在使用的 ODBC 驅動程式支援靜態資料指標時，才可使用快照集。  
  
> [!NOTE]
>  對於某些 ODBC 驅動程式來說，快照集 \(靜態資料指標\) 可能會不可更新。  檢查您的驅動程式文件，了解可支援的資料指標類型以及其所支援的並行類型。  若要保證可更新的快照集，請在建立 `CDatabase` 物件時確定有將資料指標程式庫載入記憶體。  如需詳細資訊，請參閱 [ODBC：ODBC 資料指標程式庫](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
> [!NOTE]
>  如果您想要使用快照集和動態集，就必須將它們建立在兩個不同的 `CDatabase` 物件上 \(兩種不同的連接\)。  
  
 如需快照集和所有資料錄集共用屬性的詳細資訊，請參閱[資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)。  如需 ODBC 和快照集以及包含 ODBC 資料指標程式庫的詳細資訊，請參閱 [ODBC](../../data/odbc/odbc-basics.md)。  
  
## 請參閱  
 [開放式資料庫連接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)