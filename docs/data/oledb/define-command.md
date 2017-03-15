---
title: "DEFINE_COMMAND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEFINE_COMMAND"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DEFINE_COMMAND 巨集"
ms.assetid: 9d724968-e242-413c-9a13-e7175fccf9b1
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# DEFINE_COMMAND
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定將用來建立資料列時， [CCommand](../../data/oledb/ccommand-class.md) 類別中的命令。  只接受字串輸入符合指定的應用程式類型 \(ANSI 或 Unicode\)。  
  
> [!NOTE]
>  建議您使用 [DEFINE\_COMMAND\_EX](../../data/oledb/define-command-ex.md) 取代 `DEFINE_COMMAND`。  
  
## 語法  
  
```  
  
DEFINE_COMMAND(  
x  
,   
szCommand  
 )  
  
```  
  
#### 參數  
 *x*  
 \[in\] 使用者資料錄\(命令\)類別的名稱。  
  
 `szCommand`  
 \[in\]將用來建立資料列集， [CCommand](../../data/oledb/ccommand-class.md)時的命令字串。  
  
## 備註  
 您指定的命令字串會當預設值，如果您在 [CCommand::Open](../../data/oledb/ccommand-open.md) 方法不指定命令文字。  
  
 這個巨集接受 ANSI 字串，當您建置應用程式，為 ANSI 或 Unicode 字串，如果您建立自己的應用程式為 Unicode。  建議您使用 [DEFINE\_COMMAND\_EX](../../data/oledb/define-command-ex.md) ，而不是 `DEFINE_COMMAND`，因為前接受 Unicode 字串，不論 ANSI 或 Unicode 應用程式類型。  
  
## 範例  
 請參閱 [BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [OLE DB 消費者樣板的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)