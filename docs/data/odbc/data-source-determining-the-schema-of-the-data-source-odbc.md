---
title: "資料來源：決定資料來源的結構描述 (ODBC) | Microsoft Docs"
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
  - "資料來源 [C++], 決定結構描述"
  - "ODBC 資料來源 [C++], 結構描述"
  - "結構描述 [C++], 資料來源"
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 資料來源：決定資料來源的結構描述 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 若要在您的 `CRecordset` 物件設定資料成員，您需要知道將要連接資料來源的結構描述 \(Schema\)。  決定資料來源的結構描述，會牽涉到取得資料來源的資料表清單、每個資料表的資料行清單、每個資料行的資料型別和任何存在的索引。  
  
## 請參閱  
 [資料來源 \(ODBC\)](../../data/odbc/data-source-odbc.md)   
 [資料來源：管理連接 \(ODBC\)](../../data/odbc/data-source-managing-connections-odbc.md)