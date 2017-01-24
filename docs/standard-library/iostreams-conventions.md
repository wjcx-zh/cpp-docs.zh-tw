---
title: "iostreams 慣例 | Microsoft Docs"
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
  - "iostream 標頭"
  - "Standard C++ 程式庫, iostreams"
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
caps.latest.revision: 10
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# iostreams 慣例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

iostreams 標頭支援文字之間的轉換並輸入表單輸入和輸出到外部檔案:  
  
|||  
|-|-|  
|[\<fstream\>](../standard-library/fstream.md)|[\< \> iomanip](../standard-library/iomanip.md)|  
|[\<ios\>](../standard-library/ios.md)|[\<iosfwd\>](../standard-library/iosfwd.md)|  
|[\<iostream\>](../standard-library/iostream.md)|[\< \> istream](../standard-library/istream.md)|  
|[\<ostream\>](../standard-library/ostream.md)|[\<sstream\>](../standard-library/sstream.md)|  
|[\< \> streambuf](../standard-library/streambuf.md)|[\<strstream\>](../standard-library/strstream.md)|  
  
 對 iostreams 的最簡單用法只需要包含 Header [\<iostream\>](../standard-library/iostream.md)。  您可以從 [cin](../Topic/cin.md) 或 [wcin](../Topic/wcin.md) 然後擷取值讀取標準輸入。  這樣做的規則在類別 [basic\_istream 類別](../standard-library/basic-istream-class.md)的說明所示。  您也可以將值設為 [cout](../Topic/cout.md) 或 [wcout](../Topic/wcout.md) 寫入標準輸出。  這樣做的規則在類別 [basic\_ostream 類別](../standard-library/basic-ostream-class.md)的說明所示。  對兩個擷取器和 insertors 表單控制項的共用類別 [basic\_ios 類別](../standard-library/basic-ios-class.md)處理。  作業的扮取此格式資訊和插入物件是幾個操作工具使用。  
  
 您可以針對您依名稱要開啟檔案的相同 iostreams 作業，使用宣告的類別在 [\<fstream\>](../standard-library/fstream.md)。  若要轉換類別之間 [basic\_string 類別](../standard-library/basic-string-class.md)iostreams 和物件，請使用宣告的類別在 [\<sstream\>](../standard-library/sstream.md)。  若要執行相同 C 字串，請使用宣告的類別在 [\<strstream\>](../standard-library/strstream.md)。  
  
 其餘的標題為 iostreams 類別的只有最進階使用者提供支援服務，功能直接相關。  
  
## 請參閱  
 [STL 概觀](../standard-library/cpp-standard-library-overview.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)