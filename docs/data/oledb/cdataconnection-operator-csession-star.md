---
title: "CDataConnection::operator CSession* | Microsoft Docs"
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
  - "CDataConnection.operatorCSession*"
  - "CDataConnection::operatorCSession*"
  - "operatorCSession*"
  - "CSession*"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSession* operator"
  - "operator CSession*"
ms.assetid: 0b0feede-5c3e-4835-be5b-03651597014d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::operator CSession*
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回 `CSession` 物件的指標。  
  
## 語法  
  
```  
  
operator const CSession*() throw( );  
  
```  
  
## 備註  
 這個運算子會傳回包含 `CSession` 物件的指標，可讓您傳遞 `CSession` 指標所需於 `CDataConnection` 物件。  
  
## 範例  
 使用方式範例請參閱 [運算子 CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md) 。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md)