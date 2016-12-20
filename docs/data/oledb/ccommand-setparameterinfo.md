---
title: "CCommand::SetParameterInfo | Microsoft Docs"
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
  - "SetParameterInfo"
  - "CCommand.SetParameterInfo"
  - "CCommand::SetParameterInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetParameterInfo 方法"
ms.assetid: a70e92f4-1e73-41d7-a5b7-c6ebb45a6477
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCommand::SetParameterInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定每個命令參數的原生型別。  
  
## 語法  
  
```  
  
      HRESULT CCommandBase::SetParameterInfo(  
   DB_UPARAMS ulParams,  
   const DBORDINAL* pOrdinals,  
   const DBPARAMBINDINFO* pParamInfo   
) throw( );  
```  
  
#### 參數  
 請參閱 *OLE DB Programmer's Reference* 中的 [ICommandWithParameters::SetParameterInfo](https://msdn.microsoft.com/en-us/library/ms725393.aspx)。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)