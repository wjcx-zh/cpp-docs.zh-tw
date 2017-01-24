---
title: "VERSION (C/C++) | Microsoft Docs"
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
  - "VERSION"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VERSION .def 檔案陳述式"
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# VERSION (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

告訴 LINK 在 .exe 檔或 DLL 的標題中放置一個數字。  
  
```  
VERSION major[.minor]  
```  
  
## 備註  
 *major* 和 *minor* 引數是 0 到 65,535 之間的十進位數字。  預設值為 0.0 版。  
  
 指定版本號碼的另一種方式是使用[版本資訊](../../build/reference/version-version-information.md) \(\/VERSION\) 選項。  
  
## 請參閱  
 [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)