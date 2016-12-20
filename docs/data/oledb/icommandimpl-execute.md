---
title: "ICommandImpl::Execute | Microsoft Docs"
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
  - "ICommandImpl::Execute"
  - "ICommandImpl.Execute"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Execute 方法"
ms.assetid: 033e0d4e-256b-4eed-9215-70e0bebb768c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandImpl::Execute
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行命令。  
  
## 語法  
  
```  
  
      HRESULT Execute(  
   IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset   
);  
```  
  
#### 參數  
 請參閱 *OLE DB 程式設計人員參考* 中的 [ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx)。  
  
## 備註  
 要求的輸出介面將為這個函式所建立的資料列集物件中所具有的介面。  
  
 **Execute** 呼叫 [CreateRowset](../../data/oledb/icommandimpl-createrowset.md)。  覆寫預設實作來建立一個以上的資料列集，或為了建立不同的資料列集來提供您的情況。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [ICommandImpl 類別](../../data/oledb/icommandimpl-class.md)   
 [ICommandImpl::CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)