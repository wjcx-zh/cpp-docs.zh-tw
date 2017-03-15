---
title: "CDataConnection::operator CSession&amp; | Microsoft Docs"
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
  - "CSession&"
  - "CDataConnection::operatorCSession&"
  - "CDataConnection.operatorCSession&"
  - "operatorCSession&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSession& operator"
  - "operator CSession&"
ms.assetid: fba1e498-e482-4dda-8e0f-2542163bf627
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::operator CSession&amp;
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回包含於 `CSession` 物件的參考。  
  
## 語法  
  
```  
  
operator const CSession&();  
  
```  
  
## 備註  
 這個運算子會傳回包含於 `CSession` 物件的參考，可讓您透過 `CSession` 參考所需的 `CDataConnection` 物件。  
  
## 範例  
 如果您有一個函式 \(例如下面 `func` \) 會採用 `CSession` 參考，您可以使用 **CSession&** 透過 `CDataConnection` 物件。  
  
 [!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/CPP/cdataconnection-operator-csession-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/CPP/cdataconnection-operator-csession-amp_2.cpp)]  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession\*](../../data/oledb/cdataconnection-operator-csession-star.md)