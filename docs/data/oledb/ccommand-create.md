---
title: "CCommand::Create | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CCommand.Create"
  - "CCommand::Create"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Create 方法 [C++]"
ms.assetid: e4bede7a-68bd-491a-97f4-89b03d45cd24
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CCommand::Create
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

呼叫 [CCommand::CreateCommand](../../data/oledb/ccommand-createcommand.md) 建立指定的工作階段的命令，然後呼叫 [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) 指定命令文字。  
  
## 語法  
  
```  
  
      HRESULT CCommandBase::Create(  
   const CSession& session,   
   LPCWSTR wszCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT  
) throw ( );  
HRESULT CCommandBase::Create(  
   const CSession& session,   
   LPCSTR szCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT  
) throw ( );  
```  
  
#### 參數  
 `session`  
 \[之工作階段建立命令的。  
  
 `wszCommand`  
 \[\] 命令字串的 Unicode 文字的指標。  
  
 `szCommand`  
 \[\] 命令字串的 ANSI 文字的指標。  
  
 `guidCommand`  
 \[在解析指定語法和一般規則以提供者可以使用命令文字中的 GUID。  如需方言的說明，請參閱《 *OLE DB 程式設計人員參考》的*[ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) 。  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 備註  
 **Create** 第一個表單接受 Unicode 命令字串。  **Create** 第二個表單接受 ANSI 命令字串 \(隨相容性現有 ANSI 應用程式\)。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)