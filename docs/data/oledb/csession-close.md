---
title: "CSession::Close | Microsoft Docs"
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
  - "CSession::Close"
  - "ATL.CSession.Close"
  - "CSession.Close"
  - "ATL::CSession::Close"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Close 方法"
ms.assetid: dc36c4c0-e588-4c0b-91d1-fc7dc5c8e7f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSession::Close
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

結束工作階段， [CSession::Open](../../data/oledb/csession-open.md)開始。  
  
## 語法  
  
```  
  
void Close( ) throw( );  
  
```  
  
## 備註  
 釋放 **m\_spOpenRowset** 指標。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CSession 類別](../../data/oledb/csession-class.md)