---
title: "CDataConnection::operator CDataSource* | Microsoft Docs"
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
  - "CDataSource*"
  - "CDataConnection::operatorCDataSource*"
  - "CDataConnection.operatorCDataSource*"
  - "operatorCDataSource*"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDataSource* operator"
  - "operator * (CDataSource)"
ms.assetid: 9118e324-e68d-45c5-a791-03f041d420ed
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::operator CDataSource*
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回 `CDataSource` 物件的指標。  
  
## 語法  
  
```  
  
operator const CDataSource*() throw( );  
  
```  
  
## 備註  
 這個運算子會傳回包含 `CDataSource` 物件的指標，可讓您傳遞 `CDataSource` 指標所需於 `CDataConnection` 物件。  
  
 使用方式範例請參閱 [運算子 CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) 。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)