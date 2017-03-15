---
title: "資料來源和工作階段 | Microsoft Docs"
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
  - "連接 [C++], 資料來源"
  - "資料來源 [C++], OLE DB"
  - "OLE DB 消費者樣板 [C++], 資料來源"
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 資料來源和工作階段
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下圖顯示了可以支援資料來源連接和存取的類別。  每個類別都是根據標準 OLE DB 元件的實作。  
  
 ![資料來源和工作階段類別](../../data/oledb/media/vcdatasourcesessionclasses.png "vcDataSourceSessionClasses")  
資料來源和工作階段類別  
  
 這些類別是：  
  
-   [CDataSource](../../data/oledb/cdatasource-class.md)：這個類別會產生資料來源物件，該物件會透過 OLE DB 提供者 \(Provider\) 建立和管理資料來源的連接。  資料來源會以連接字串 \(Connection String\) 形式取得如資料來源位址和驗證資訊的資訊。  
  
     值得注意的是，Helper 類別 [CEnumerator](../../data/oledb/cenumerator-class.md) 在任何連接建立之前，經常會用來取得已登錄於系統中的可用提供者之清單。  這樣您便可以像選取資料來源一樣地選取提供者。  例如，\[**資料連結內容**\] 對話方塊會在 \[提供者\] 索引標籤使用這個類別來填入 \(Populate\) 提供者清單。  它的作用相當於 **SQLBrowseConnect** 或 **SQLDriverConnect** 函式。  
  
-   [CSession](../../data/oledb/csession-class.md)：這個類別會產生工作階段物件，此物件可以代表該資料來源的單一存取工作階段。  但是，您也可以在資料來源上建立多個工作階段。  您可以針對每個工作階段，建立其資料列集、命令和其他物件，以存取資料來源的資料。  此工作階段可以處理交易。  
  
## 請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)