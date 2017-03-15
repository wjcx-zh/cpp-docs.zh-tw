---
title: "CCommand::CreateCommand | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CCommand.CreateCommand"
  - "CreateCommand"
  - "CCommand::CreateCommand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateCommand 方法"
ms.assetid: 3652a313-07a1-40ec-82d6-fc7182f2a6f6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CCommand::CreateCommand
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立新命令。  
  
## 語法  
  
```  
  
      HRESULT CCommandBase::CreateCommand(  
   const CSession& session   
) throw ( );  
```  
  
#### 參數  
 `session`  
 \[in\] 與新的命令相關聯的 `CSession` 物件。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 這個方法使用指定的工作階段物件建立命令。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)