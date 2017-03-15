---
title: "CBookmark::SetBookmark | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CBookmark<0>::SetBookmark"
  - "ATL.CBookmark<0>.SetBookmark"
  - "CBookmark<0>.SetBookmark"
  - "SetBookmark"
  - "ATL::CBookmark::SetBookmark"
  - "ATL::CBookmark<0>::SetBookmark"
  - "CBookmark.SetBookmark"
  - "ATL.CBookmark.SetBookmark"
  - "CBookmark::SetBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetBookmark 方法"
ms.assetid: bcd26831-6045-4e69-96d6-abf8037fc18d
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CBookmark::SetBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

複製 `pBuffer` 參考的書籤值對 `CBookmark` 緩衝區並將緩衝區大小設定為 `nSize`。  
  
## 語法  
  
```  
  
      HRESULT SetBookmark(  
   DBLENGTH nSize,  
   BYTE* pBuffer   
) throw( );  
```  
  
#### 參數  
 *nSize*  
 \[書籤緩衝區的大小。  
  
 `pBuffer`  
 \[out 包含書籤值的位元組陣列中的指標。  
  
## 傳回值  
 標準 `HRESULT`。  
  
## 備註  
 這個函式只能在 **CBookmark\<0\>**。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CBookmark 類別](../../data/oledb/cbookmark-class.md)