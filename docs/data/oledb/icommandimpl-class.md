---
title: "ICommandImpl 類別 | Microsoft Docs"
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
  - "ICommandImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandImpl 類別"
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

針對 [ICommand](https://msdn.microsoft.com/en-us/library/ms709737.aspx) 介面的實作。  
  
## 語法  
  
```  
template <class T, class CommandBase = ICommand>   
class ATL_NO_VTABLE ICommandImpl : public CommandBase  
```  
  
#### 參數  
 `T`  
 您的類別，衍生自 `ICommandImpl`。  
  
 `CommandBase`  
 的命令介面。  預設為 `ICommand`。  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[CancelExecution](../../data/oledb/icommandimpl-cancelexecution.md)|取消目前的命令執行。|  
|[取消](../../data/oledb/icommandimpl-cancel.md)|取消目前的命令執行。|  
|[CreateRowset](../../data/oledb/icommandimpl-createrowset.md)|建立資料列集物件。|  
|[執行](../../data/oledb/icommandimpl-execute.md)|執行命令。|  
|[GetDBSession](../../data/oledb/icommandimpl-getdbsession.md)|傳回介面指標建立命令的工作階段。|  
|[ICommandImpl](../../data/oledb/icommandimpl-icommandimpl.md)|建構函式。|  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_bCancel](../../data/oledb/icommandimpl-m-bcancel.md)|表示命令是否要取消。|  
|[m\_bCancelWhenExecuting](../../data/oledb/icommandimpl-m-bcancelwhenexecuting.md)|表示命令是否要取消，在執行時執行的。|  
|[m\_bIsExecuting](../../data/oledb/icommandimpl-m-bisexecuting.md)|表示命令目前是否正在執行。|  
  
## 備註  
 在命令物件上必須的介面。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)