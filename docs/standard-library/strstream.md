---
title: "&lt;strstream&gt; | Microsoft Docs"
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
  - "std.<strstream>"
  - "std::<strstream>"
  - "<strstream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strstream 標頭"
ms.assetid: eaa9d0d4-d217-4f28-8a68-9b9ad7b1c0f5
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;strstream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義可為已配置的 `char` 物件陣列所儲存之序列的 iostreams 作業提供支援的數個類別。  這類序列會輕易地與 C 字串相互轉換。  
  
## 語法  
  
```  
  
#include <strstream>  
  
```  
  
## 備註  
 類型 `strstream` 的物件可與 `char` \* \(是 C 字串\) 搭配運作。  使用 [\<sstream\>](../standard-library/sstream.md) 可與類型 type [basic\_string](../standard-library/basic-string-class.md) 的物件搭配運作。  
  
> [!NOTE]
>  `<strstream>` 中的類別已被取代。  請考慮改用 `<sstream>` 中的類別。  
  
### 類別  
  
|||  
|-|-|  
|[strstreambuf 類別](../standard-library/strstreambuf-class.md)|此類別說明一個資料流緩衝區，它可控制元素與 `char` 陣列物件中儲存的元素序列之間的相互傳輸。|  
|[istrstream 類別](../standard-library/istrstream-class.md)|此類別說明會控制如何從類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區中擷取元素和編碼物件的物件。|  
|[ostrstream 類別](../standard-library/ostrstream-class.md)|此類別說明會控制如何在類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區中插入元素和編碼物件的物件。|  
|[strstream 類別](../standard-library/strstream-class.md)|此類別說明會控制如何使用類別 [strstreambuf](../standard-library/strstreambuf-class.md) 的資料流緩衝區來插入及擷取元素和編碼物件的物件。|  
  
## 請參閱  
 [\<strstream\>](../standard-library/strstream.md)   
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)