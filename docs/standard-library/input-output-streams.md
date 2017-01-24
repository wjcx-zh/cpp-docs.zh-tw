---
title: "輸入/輸出資料流 | Microsoft Docs"
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
  - "I/O [C++], 資料流"
  - "資料流 I/O"
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
caps.latest.revision: 11
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 輸入/輸出資料流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`basic_iostream`，位於標 \<頭檔 istream\>定義，是處理輸入和輸出以字元為主的 I\/O 資料流物件的類別樣板。  
  
 取得定義 `basic_iostream` 字元特定特製化，而且可以讓程式碼更容易閱讀的兩個 typedef: `iostream` \(與標頭檔 iostream \<\>混淆\) 是根據 `basic_iostream<char>`的 I\/O 資料流; `wiostream` 是根據 `basic_iostream<wchar_t>`的 I\/O 資料流。  
  
 如需詳細資訊，請參閱[basic\_iostream 類別](../standard-library/basic-iostream-class.md)、[iostream](../Topic/iostream.md) 和 [wiostream](../Topic/wiostream.md)。  
  
 衍生自 `basic_iostream` 的類別樣板 `basic_fstream`，用於從檔案資料流的字元資料。  
  
 也有提供 `basic_fstream`的字元特定特製化的 Typedef。  它們是 `fstream`，這是檔案 I\/O 資料流根據 `char`和 `wfstream`，為檔案 I\/O 資料流以 `wchar_t`為基礎。  如需詳細資訊，請參閱[basic\_fstream 類別](../standard-library/basic-fstream-class.md)、[fstream](../Topic/fstream.md) 和 [wfstream](../Topic/wfstream.md)。  使用這些 Typedef 要求標頭檔 \<fstream\>中。  
  
> [!NOTE]
>  當 `basic_fstream` 物件用來執行檔案 I\/O 時，不過，基礎緩衝區包含讀取和寫入的個別指定的位置，目前項目和目前輸出位置的繫結，因此，讀取某些資料移動輸出位置。  
  
 類別樣板 `basic_stringstream` 和其共同的特製化，則為 `stringstream`，通常與 I\/O 資料流物件一起使用插入和擷取字元資料。  如需詳細資訊，請參閱[basic\_stringstream 類別](../standard-library/basic-stringstream-class.md)。  
  
## 請參閱  
 [stringstream](../Topic/stringstream.md)   
 [basic\_stringstream 類別](../standard-library/basic-stringstream-class.md)   
 [\<sstream\>](../standard-library/sstream.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [C\+\+ Standard Library](../standard-library/cpp-standard-library-reference.md)