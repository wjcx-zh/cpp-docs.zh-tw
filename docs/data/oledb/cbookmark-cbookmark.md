---
title: "CBookmark::CBookmark | Microsoft Docs"
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
  - "CBookmark<0>.CBookmark<0>"
  - "CBookmark::CBookmark"
  - "ATL.CBookmark.CBookmark"
  - "CBookmark.CBookmark"
  - "CBookmark"
  - "ATL::CBookmark<0>::CBookmark<0>"
  - "ATL.CBookmark<0>.CBookmark<0>"
  - "CBookmark<0>::CBookmark<0>"
  - "ATL::CBookmark::CBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBookmark 類別, 建構函式"
ms.assetid: 84f4ad2b-67d4-4ba3-8b2b-656a66fb6298
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBookmark::CBookmark
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建構函式。  
  
## 語法  
  
```  
  
      CBookmark( );   
CBookmark(  
   DBLENGTH nSize   
);  
```  
  
#### 參數  
 `nSize`  
 \[in\] 呼叫書籤的大小 \(以位元組為單位\)。  
  
## 備註  
 第一個函式會將設定 **NULL** 的緩衝區、緩衝區大小設定為 0。  第二個函式會對 `nSize`的緩衝區大小和至位元組陣列的緩衝區 `nSize` 位元組。  
  
> [!NOTE]
>  這個函式只能在 **CBookmark\<0\>**。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CBookmark 類別](../../data/oledb/cbookmark-class.md)