---
title: "ICommandTextImpl::GetCommandText | Microsoft Docs"
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
  - "GetCommandText"
  - "ICommandTextImpl.GetCommandText"
  - "ICommandTextImpl::GetCommandText"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetCommandText 方法"
ms.assetid: 0f8da470-b1c3-4573-974f-1acc111e3984
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandTextImpl::GetCommandText
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

由最後一個呼叫傳回文字命令設定為 [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)。  
  
## 語法  
  
```  
  
      STDMETHOD(GetCommandText)(   
   GUID * pguidDialect,   
   LPOLESTR * ppwszCommand    
);  
```  
  
#### 參數  
 請參閱 *OLE DB 程式設計人員參考* 中的 [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx)。  根據預設 *pguidDialect* 參數被忽略。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [ICommandTextImpl 類別](../../data/oledb/icommandtextimpl-class.md)