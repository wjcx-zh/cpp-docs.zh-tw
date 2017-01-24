---
title: "IConvertTypeImpl::CanConvert | Microsoft Docs"
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
  - "IConvertTypeImpl.CanConvert"
  - "CanConvert"
  - "IConvertTypeImpl::CanConvert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanConvert 方法"
ms.assetid: bdad6e95-bc0b-4427-9b5e-eea51f09f392
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IConvertTypeImpl::CanConvert
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供型別轉換的可用性的資訊列在命令或。  
  
## 語法  
  
```  
  
      STDMETHOD(CanConvert)(   
   DBTYPE wFromType,   
   DBTYPE wToType,   
   DBCONVERTFLAGS dwConvertFlags    
);  
```  
  
#### 參數  
 請參閱《 *OLE DB 程式設計人員參考》的*[IConvertType::CanConvert](https://msdn.microsoft.com/en-us/library/ms711224.aspx) 。  
  
## 備註  
 用於 `MSADC.DLL`的 OLE DB 資料轉換。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [IConvertTypeImpl 類別](../../data/oledb/iconverttypeimpl-class.md)