---
title: "動態集的 ODBC 驅動程式需求 | Microsoft Docs"
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
  - "驅動程式, 動態集"
  - "驅動程式, ODBC"
  - "動態集"
  - "ODBC 驅動程式, 動態集"
  - "ODBC 資料錄集, 動態集"
  - "資料錄集, 動態集"
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 動態集的 ODBC 驅動程式需求
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 MFC ODBC 資料庫類別中，動態集 \(Dynaset\) 是具有動態屬性的資料錄集；它們會以特定方式與資料來源保持同步。  MFC 動態集 \(但不適用順向 \(Forward\-only\) 資料錄集\) 需要使用具有層級 2 之 API 一致性的 ODBC 驅動程式。  若您的[資料來源](../../data/odbc/data-source-odbc.md)使用的驅動程式符合層級 1 之 API 集，就仍然可以同時使用可更新和唯讀的快照集和順向的資料錄集，但不能使用動態集。  儘管如此，層級 1 的驅動程式可以在其支援擴充擷取和索引鍵集驅動的資料指標時，支援動態集。  
  
 在 ODBC 詞彙中，動態集和快照集都是指資料指標。  資料指標是一種可用於儲存其在資料錄集位置的機制。  如需動態集驅動程式需求的詳細資訊，請參閱[動態集](../../data/odbc/dynaset.md)。  如需資料指標的詳細資訊，請參閱 MSDN 文件中的[開放式資料庫連接 \(ODBC\)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) SDK。  
  
> [!NOTE]
>  若要使用可更新的資料錄集，您的 ODBC 驅動程式必須支援定位更新陳述式，或是 **::SQLSetPos** ODBC API 函式。  MFC 會在兩者都可支援情況下，使用效能較高的 **::SQLSetPos**。  另一種針對快照集的做法是使用資料指標程式庫，其可提供可更新快照集所需的支援 \(靜態資料指標和定位更新陳述式\)。  
  
## 請參閱  
 [ODBC 的基本概念](../../data/odbc/odbc-basics.md)