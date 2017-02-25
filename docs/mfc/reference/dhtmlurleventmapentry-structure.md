---
title: "DHtmlUrlEventMapEntry 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DHtmlUrlEventMapEntry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DHtmlUrlEventMapEntry 結構"
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# DHtmlUrlEventMapEntry 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`DHtmlUrlEventMapEntry` 結構提供多個 URL 的事件對應支援。  
  
## 語法  
  
```  
  
      struct DHtmlUrlEventMapEntry  
{  
   LPCTSTR szUrl;  
   const DHtmlEventMapEntry *pEventMap;  
};  
```  
  
#### 參數  
 `szUrl`  
 URL。  
  
 *pEventMap*  
 與 URL 關聯的事件對應。  
  
## 需求  
 **標頭檔：** afxdhtml.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)