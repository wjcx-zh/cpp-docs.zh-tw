---
title: "tlbid | Microsoft Docs"
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
  - "tlbid"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tlbid 屬性"
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tlbid
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 允許載入主要類型程式庫以外的程式庫。  
  
## 語法  
  
```  
tlbid(number)  
```  
  
#### 參數  
 `number`  
 `filename` 中類型程式庫的號碼。  
  
## 備註  
 如果有多個類型程式庫內建於單一 DLL 中，它可能會使用 `tlbid` 載入主要類型程式庫以外的程式庫。  
  
 例如：  
  
```  
#import <MyResource.dll> tlbid(2)  
```  
  
 等於：  
  
```  
LoadTypeLib("MyResource.dll\\2");  
```  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)