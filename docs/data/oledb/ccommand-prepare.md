---
title: "CCommand::Prepare | Microsoft Docs"
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
  - "CCommand.Prepare"
  - "CCommand::Prepare"
  - "Prepare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Prepare 方法"
ms.assetid: f0e473fc-2f7a-4d29-96c2-1328dc21e702
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCommand::Prepare
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

驗證並最佳化目前命令。  
  
## 語法  
  
```  
  
      HRESULT CCommandBase::Prepare(  
   ULONG cExpectedRuns = 0   
) throw( );  
```  
  
#### 參數  
 *cExpectedRuns*  
 \[您預期執行命令的次數。  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 備註  
 這個方法會包裝 OLE DB 方法 [ICommandPrepare::Prepare](https://msdn.microsoft.com/en-us/library/ms718370.aspx)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)