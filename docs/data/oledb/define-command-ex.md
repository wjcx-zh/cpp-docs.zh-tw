---
title: "DEFINE_COMMAND_EX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEFINE_COMMAND_EX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DEFINE_COMMAND_EX 巨集"
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# DEFINE_COMMAND_EX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定將用來建立資料列時， [CCommand](../../data/oledb/ccommand-class.md) 類別中的命令。  支援 ANSI 和 Unicode 應用程式。  
  
## 語法  
  
```  
  
DEFINE_COMMAND_EX(  
x  
,   
wszCommand  
 )  
  
```  
  
#### 參數  
 *x*  
 \[使用者資料錄 \(\) 命令類別的名稱。  
  
 `wszCommand`  
 \[\] 將用來建立資料列集， [CCommand](../../data/oledb/ccommand-class.md)時的命令字串。  
  
## 備註  
 您指定的命令字串會當預設值，如果您在 [CCommand::Open](../../data/oledb/ccommand-open.md) 方法不指定命令文字。  
  
 不論應用程式類型，此巨集接受 Unicode 字串。  因為它支援 Unicode 和 ANSI 應用程式，這個巨集會優先於 [DEFINE\_COMMAND](../../data/oledb/define-command.md) 。  
  
## 範例  
 請參閱 [BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)