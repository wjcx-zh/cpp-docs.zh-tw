---
title: "CCommand::GetParameterInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetParameterInfo"
  - "CCommand.GetParameterInfo"
  - "CCommand::GetParameterInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetParameterInfo 方法"
ms.assetid: 9cd9277f-0161-4bd8-ad24-58e5e90b92a7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CCommand::GetParameterInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得命令的參數、其名稱和它們的型別清單。  
  
## 語法  
  
```  
  
      HRESULT CCommandBase::GetParameterInfo(  
   DB_UPARAMS* pParams,  
   DBPARAMINFO** ppParamInfo,  
   OLECHAR** ppNamesBuffer   
) throw ( );  
```  
  
#### 參數  
 請參閱 *OLE DB Programmer's Reference* 中的 [ICommandWithParameters::GetParameterInfo](https://msdn.microsoft.com/en-us/library/ms714917.aspx)。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)