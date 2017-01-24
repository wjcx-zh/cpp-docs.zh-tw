---
title: "CDataConnection::CDataConnection | Microsoft Docs"
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
  - "CDataConnection.CDataConnection"
  - "ATL.CDataConnection.CDataConnection"
  - "CDataConnection::CDataConnection"
  - "ATL::CDataConnection::CDataConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataConnection 類別, 建構函式"
ms.assetid: ac25c9a0-44d3-4083-b13f-76c07772e12d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::CDataConnection
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行個體化及初始化 `CDataConnection` 物件。  
  
## 語法  
  
```  
  
      CDataConnection();   
CDataConnection(  
   const CDataConnection &ds  
);  
```  
  
#### 參數  
 `ds`  
 \[in\] 現有資料連接的參考。  
  
## 備註  
 第一個覆寫建立具有預設值的新 `CDataConnection` 物件。  
  
 第二個覆寫建立與您指定之資料連接物件的設定相同的新的 `CDataConnection` 物件。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)