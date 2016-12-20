---
title: "CManualAccessor 類別 | Microsoft Docs"
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
  - "ATL::CManualAccessor"
  - "ATL.CManualAccessor"
  - "CManualAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CManualAccessor 類別"
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CManualAccessor 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示為進階使用方式設計的存取子型別。  
  
## 語法  
  
```  
class CManualAccessor : public CAccessorBase  
```  
  
## 成員  
  
### 方法  
  
|||  
|-|-|  
|[AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)|將繫結項目加入輸出資料行。|  
|[AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)|將參數輸入到參數存取子。|  
|[CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md)|資料繫結配置記憶體結構和初始化的資料成員。|  
|[CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md)|參數繫結配置記憶體結構和初始化的參數成員。|  
  
## 備註  
 使用 `CManualAccessor`，您可以透過執行階段函式呼叫指定參數和輸出資料行繫結。  
  
## 需求  
 **標頭：** atldbcli.h  
  
## 請參閱  
 [DBViewer](../../top/visual-cpp-samples.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)