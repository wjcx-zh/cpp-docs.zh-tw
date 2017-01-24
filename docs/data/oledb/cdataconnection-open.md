---
title: "CDataConnection::Open | Microsoft Docs"
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
  - "CDataConnection.Open"
  - "ATL.CDataConnection.Open"
  - "CDataConnection::Open"
  - "ATL::CDataConnection::Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open 方法"
ms.assetid: 2c6f0c01-4954-43ba-973e-861ac8e82892
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDataConnection::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用初始化字串，開啟與資料來源的連接。  
  
## 語法  
  
```  
  
      HRESULT Open(   
   LPCOLESTR szInitString    
) throw( );  
```  
  
#### 參數  
 *szInitString*  
 \[in\] 資料來源初始化字串。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDataConnection 類別](../../data/oledb/cdataconnection-class.md)