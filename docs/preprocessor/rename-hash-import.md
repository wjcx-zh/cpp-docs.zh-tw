---
title: "rename (#import) | Microsoft Docs"
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
  - "Rename"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "重新命名屬性"
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rename (#import)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 專有的**  
  
 解決名稱衝突問題。  
  
## 語法  
  
```  
rename("OldName","NewName")  
```  
  
#### 參數  
 `OldName`  
 類型程式庫中的舊名稱。  
  
 `NewName`  
 用來取代舊名稱的名稱。  
  
## 備註  
 如果指定此屬性，編譯器會在產生的標頭檔中，以使用者提供的 *NewName* 取代出現在類型程式庫中的所有 *OldName*。  
  
 當類型程式庫中的名稱與系統標頭檔中的巨集定義相符時，才能使用這個屬性。  如果此情況未解決，則會產生各種語法錯誤，例如[編譯器錯誤 C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) 和 [編譯器錯誤 C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md)。  
  
> [!NOTE]
>  取代適用於類型程式庫中使用的名稱，不適用於所產生標頭檔中使用的名稱。  
  
 例如，假設屬性名稱 `MyParent` 存在於類型程式庫中，而標頭檔中已定義巨集 `GetMyParent`，且已在 `#import` 之前使用。  由於 `GetMyParent` 是包裝函式的預設名稱，在進行 **get** 屬性的錯誤處理時，就會發生名稱衝突。  若要解決此問題，請在 `#import` 陳述式中使用下列屬性：  
  
```  
rename("MyParent","MyParentX")  
```  
  
 其中會重新命名類型程式庫中的名稱 `MyParent`。  嘗試重新命名 `GetMyParent` 包裝函式名稱將會失敗：  
  
```  
rename("GetMyParent","GetMyParentX")  
```  
  
 這是因為名稱 `GetMyParent` 只會出現在產生的類型程式庫標頭檔中。  
  
 **END C\+\+ 特定的**  
  
## 請參閱  
 [\#import 屬性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指示詞](../preprocessor/hash-import-directive-cpp.md)