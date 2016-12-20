---
title: "NAME (C/C++) | Microsoft Docs"
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
  - "name"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NAME .def 檔案陳述式"
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# NAME (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定主要輸出檔的名稱。  
  
```  
NAME [application][BASE=address]  
```  
  
## 備註  
 指定輸出檔名稱的另一種方式是使用 [\/OUT](../../build/reference/out-output-file-name.md) 連結器選項，而設定基底位址的另一種方式是使用 [\/BASE](../../build/reference/base-base-address.md) 連結器選項。  如果兩種方式都有指定，\/OUT 會覆寫 **NAME**。  
  
 如果建置 DLL，NAME 將只會影響 DLL 名稱。  
  
## 請參閱  
 [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)