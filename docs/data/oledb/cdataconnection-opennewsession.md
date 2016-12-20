---
title: "CDataConnection::OpenNewSession | Microsoft Docs"
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
  - "CDataConnection.OpenNewSession"
  - "ATL.CDataConnection.OpenNewSession"
  - "ATL::CDataConnection::OpenNewSession"
  - "OpenNewSession"
  - "CDataConnection::OpenNewSession"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenNewSession 方法"
ms.assetid: 0a70e573-9498-4ca7-b524-45666dc7b0a3
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::OpenNewSession
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用目前連接物件的資料來源，啟動新的工作階段。  
  
## 語法  
  
```  
  
      HRESULT OpenNewSession(   
   CSession & session    
) throw( );  
```  
  
#### 參數  
 `session`  
 \[in\/out\] 新工作階段物件的參考。  
  
 **備註**  
 新的工作階段使用目前連接物件中所包含的資料來源物件列為父代，並且可以存取所有資訊和資料來源相同。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)