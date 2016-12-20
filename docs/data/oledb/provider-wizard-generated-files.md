---
title: "提供者精靈產生的檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 提供者, 精靈產生的檔案"
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 提供者精靈產生的檔案
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ATL OLE DB 提供者精靈可產生下列檔案。  下列主題使用簡短名稱 "MyProvider"，不過實際檔名則視您建立提供者時所作的選擇而定。  
  
|檔案名稱|說明|  
|----------|--------|  
|MyProviderRS.cpp|包含命令 helper `Execute` 方法和提供者資料行對應。|  
|MyProviderDS.h|實作資料來源物件。  這個標頭檔包含資料來源屬性的屬性對應。|  
|MyProviderRS.h|實作命令和資料列集物件。  這個標頭檔包含資料列集和命令屬性的屬性對應。|  
|MyProviderSess.h|實作工作階段物件。  這個標頭檔包含工作階段屬性的屬性對應。|  
|MyProvider.rgs|包含 OLE DB 提供者精靈所產生的登錄物件。|  
  
## 請參閱  
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)