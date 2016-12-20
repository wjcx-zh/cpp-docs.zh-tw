---
title: "&lt;fstream&gt; | Microsoft Docs"
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
  - "std::<fstream>"
  - "<fstream>"
  - "std.<fstream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fstream 標頭"
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;fstream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義可對外部檔案中儲存之序列的 iostreams 作業提供支援的數個類別。  
  
## 語法  
  
```  
  
#include <fstream>  
  
```  
  
### Typedefs  
  
|||  
|-|-|  
|[filebuf](../Topic/filebuf.md)|根據 `char` 範本參數特製化的 `basic_filebuf` 類型。|  
|[fstream](../Topic/fstream.md)|根據 `char` 範本參數特製化的 `basic_fstream` 類型。|  
|[ifstream](../Topic/ifstream.md)|根據 `char` 範本參數特製化的 `basic_ifstream` 類型。|  
|[ofstream](../Topic/ofstream.md)|根據 `char` 範本參數特製化的 `basic_ofstream` 類型。|  
|[wfstream](../Topic/wfstream.md)|根據 `wchar_t` 範本參數特製化的 `basic_fstream` 類型。|  
|[wifstream](../Topic/wifstream.md)|根據 `wchar_t` 範本參數特製化的 `basic_ifstream` 類型。|  
|[wofstream](../Topic/wofstream.md)|根據 `wchar_t` 範本參數特製化的 `basic_ofstream` 類型。|  
|[wfilebuf](../Topic/wfilebuf.md)|根據 `wchar_t` 範本參數特製化的 `basic_filebuf` 類型。|  
  
### 類別  
  
|||  
|-|-|  
|[basic\_filebuf](../standard-library/basic-filebuf-class.md)|範本類別描述資料流緩衝區，其控制類型 **Elem** 的項目 \(其字元特性由類別 **Tr** 所決定\)，與外部檔案中儲存的項目序列之間的往來傳輸。|  
|[basic\_fstream](../standard-library/basic-fstream-class.md)|此範本類別描述一個物件，該物件可控制使用 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**\> 類別的資料流緩衝區插入及擷取項目和編碼物件、搭配 **Elem** 類型的項目，而且其字元特性是由 **Tr** 類別所決定。|  
|[basic\_ifstream](../standard-library/basic-ifstream-class.md)|此範本類別描述一個物件，該物件可控制從 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**\> 類別的資料流緩衝區擷取項目和編碼物件、搭配 **Elem** 類型的項目，而且其字元特性是由 **Tr** 類別所決定。|  
|[basic\_ofstream](../standard-library/basic-ofstream-class.md)|此範本類別描述一個物件，該物件可控制將項目和編碼物件插入 [basic\_filebuf](../standard-library/basic-filebuf-class.md)\<**Elem**, **Tr**\> 類別的資料流緩衝區、搭配 **Elem** 類型的項目，而且其字元特性是由 **Tr** 類別所決定。|  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)