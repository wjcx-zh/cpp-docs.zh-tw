---
title: "CDataConnection::operator bool (OLE DB) | Microsoft Docs"
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
  - "CDataConnection::operatorBOOL"
  - "ATL::CDataConnection::operatorBOOL"
  - "CDataConnection.operatorBOOL"
  - "ATL.CDataConnection.operatorBOOL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BOOL 運算子"
  - "運算子 bool"
ms.assetid: e0791faf-2ed2-4dbb-9e68-3b9b5da2b7a7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::operator bool (OLE DB)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷是否已在目前工作階段舉行。  
  
## 語法  
  
```  
  
operator bool( ) throw( );  
  
```  
  
## 備註  
 傳回 `bool` \(C\+\+ 資料型別\) 的值。  **true** 表示目前工作階段舉行; **false** 表示目前工作階段關閉。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator BOOL](../../data/oledb/cdataconnection-operator-bool.md)