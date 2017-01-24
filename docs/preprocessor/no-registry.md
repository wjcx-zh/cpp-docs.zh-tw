---
title: "no_registry | Microsoft Docs"
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
  - "no_registry"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "no_registry 屬性"
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# no_registry
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`no_registry` 會告知編譯器不要搜尋以 `#import` 匯入之類型程式庫的登錄。  
  
## 語法  
  
```  
  
#import filename no_registry  
```  
  
#### 參數  
 *filename*  
 類型程式庫。  
  
## 備註  
 如果在 Include 目錄中找不到參考的類型程式庫，即使該類別程式庫在登錄中，編譯仍會失敗。`no_registry` 會散佈至其他以 `auto_search` 隱含匯入的類型程式庫。  
  
 編譯器永遠不會搜尋以檔案名稱指定並直接傳遞至 `#import` 之類別程式庫的登錄。  
  
 指定 `auto_search` 時，會產生其他 `#import` 且包含初始 `#import` 的 `no_registry` 設定 \(如果最初的 `#import` 指示詞是 `no_registry`，`auto_search` 產生的 `#import` 也是 `no_registry`\)。  
  
 如果您想要匯入交互參考的類型資料庫但不要有編譯器在登錄中找到舊版檔案的風險，`no_registry` 就相當實用。`no_registry` 也非常適合用於未登錄的類型程式庫。  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)