---
title: "相依的搜尋路徑 | Microsoft Docs"
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
  - "相依性, NMAKE"
  - "NMAKE 程式, 相依性"
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 相依的搜尋路徑
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每一個相依都有選擇性的搜尋路徑，指定如下所示：  
  
## 語法  
  
```  
{directory[;directory...]}dependent  
```  
  
## 備註  
 NMAKE 會尋找在目前目錄中的第一個相依，然後按照所指定的順序在目錄中尋找。  巨集可以指定部分或所有的搜尋路徑。  以括號 \({ }\) 括住目錄名稱；如果有多個目錄，請使用分號 \(;\) 分隔。  不可以使用空格或定位字元。  
  
## 請參閱  
 [相依性](../build/dependents.md)