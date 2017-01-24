---
title: "ICommandTextImpl 類別 | Microsoft Docs"
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
  - "ICommandText"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandText 類別"
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandTextImpl 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供[ICommandText](https://msdn.microsoft.com/en-us/library/ms714914.aspx)介面的實作。  
  
## 語法  
  
```  
template <class T >  
class ATL_NO_VTABLE ICommandTextImpl   
   : public ICommandImpl<T, ICommandText>  
```  
  
#### 參數  
 `T`  
 從 **ICommandTextImpl**衍生的命令類別。  
  
## 成員  
  
### 介面方法  
  
|||  
|-|-|  
|[GetCommandText](../../data/oledb/icommandtextimpl-getcommandtext.md)|由最後一個呼叫傳回文字命令設定為 [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)。|  
|[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)|設定命令的文字，取代現有的命令文字。|  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_strCommandText](../../data/oledb/icommandtextimpl-m-strcommandtext.md)|存放區命令文字。|  
  
## 備註  
 在命令中需要的介面。  
  
## 需求  
 **Header:** altdb.h  
  
## 請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)