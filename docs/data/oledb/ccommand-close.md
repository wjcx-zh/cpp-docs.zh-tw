---
title: "CCommand::Close | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CCommand.Close"
  - "CCommand::Close"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Close 方法"
ms.assetid: 4da9c02c-7082-4e47-a0fa-78b546f0f7d2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CCommand::Close
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

釋放存取子資料列集與命令。  
  
## 語法  
  
```  
void Close( );  
```  
  
## 備註  
 命令使用一個資料列集、結果集存取子和 \(選擇性\) 參數存取子 \(不同於資料表，不支援參數，而且不需要參數存取子\)。  
  
 當您執行命令時，您應該在命令之後呼叫 `Close` 和 [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) 。  
  
 當您要重複時執行相同的命令，您也應該呼叫 `Close` 以釋放每個結果集存取子在呼叫 `Execute`之前。  本系列的最後，您也應該呼叫 `ReleaseCommand`以釋放參數存取子。  另一個常見案例呼叫具有輸出參數的預存程序。  在許多提供者 \(例如 SQL Server 的 OLE DB 提供者\) 輸出參數值無法存取，直到您關閉結果集的存取子。  呼叫 `Close` 時傳回的資料列集和結果集，存取子，但不是參數存取子，因此可讓您擷取輸出參數的值。  
  
## 範例  
 下列範例顯示當您重複地執行相同的命令時，呼叫 `Close` 和 `ReleaseCommand`。  
  
 [!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/CPP/ccommand-close_1.cpp)]  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)   
 [CCommand::ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)