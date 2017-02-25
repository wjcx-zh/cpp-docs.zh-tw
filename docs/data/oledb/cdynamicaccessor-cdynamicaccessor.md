---
title: "CDynamicAccessor::CDynamicAccessor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDynamicAccessor::CDynamicAccessor"
  - "ATL::CDynamicAccessor::CDynamicAccessor"
  - "ATL.CDynamicAccessor.CDynamicAccessor"
  - "CDynamicAccessor.CDynamicAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDynamicAccessor 類別, 建構函式"
ms.assetid: bf40fe81-2c85-473e-9075-51ad9b060b39
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CDynamicAccessor::CDynamicAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行個體化及初始化 `CDynamicAccessor` 物件。  
  
## 語法  
  
```  
  
      CDynamicAccessor(   
   DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000   
);  
```  
  
#### 參數  
 `eBlobHandling`  
 指定二進位大型物件 \(BLOB\) \(BLOB\) 資料要如何處理。  預設值為 **DBBLOBHANDLING\_DEFAULT**。  為 **DBBLOBHANDLINGENUM** 值的說明請參閱 [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) 。  
  
 `nBlobSize`  
 最大 BLOB 的大小 \(以位元組為單位\);此值的資料行視為 BLOB。  預設值為 8,000。  請參閱 [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) 以取得詳細資訊。  
  
## 備註  
 如果您使用建構函式初始化 `CDynamicAccessor` 物件，您可以指定工作會如何將繫結至 Blob。  Blob 可能包含二進位資料，例如圖形、音效或編譯的程式碼。  預設行為是將行超過 8,000 位元組為 Blob 和嘗試繫結至 `ISequentialStream` 物件。  不過，您可以指定不同的值是 BLOB 大小。  
  
 您也可以指定 `CDynamicAccessor` 如何處理資料該限定在 BLOB 資料:它可以處理 BLOB 資料的預設方法;它可以略過 \(不繫結\) BLOB 資料;也可以將提供者配置記憶體的 BLOB 資料。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)