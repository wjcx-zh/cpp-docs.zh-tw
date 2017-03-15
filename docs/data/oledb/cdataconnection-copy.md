---
title: "CDataConnection::Copy | Microsoft Docs"
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
  - "CDataConnection.Copy"
  - "ATL.CDataConnection.Copy"
  - "ATL::CDataConnection::Copy"
  - "CDataConnection::Copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Copy 方法"
ms.assetid: a3dbd70d-36be-49e0-a527-00e3910a7a56
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::Copy
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立現有資料連接的複本。  
  
## 語法  
  
```  
  
      CDataConnection& Copy(   
   const CDataConnection & ds    
) throw( );  
```  
  
#### 參數  
 `ds`  
 \[in\] 現有資料連接的參考的複本。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)