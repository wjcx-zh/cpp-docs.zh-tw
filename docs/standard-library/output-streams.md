---
title: "輸出資料流 | Microsoft Docs"
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
  - "輸出資料流"
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
caps.latest.revision: 12
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 輸出資料流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

輸出資料流物件是位元組的目的地。  三個最重要的輸出資料流類別是 `ostream`、 `ofstream`和 `ostringstream`。  
  
 `ostream` 類別，透過衍生類別 `basic_ostream`，支援預先定義的資料流物件:  
  
-   `cout` 標準輸出  
  
-   具有有限的緩衝區的`cerr` 標準錯誤  
  
-   `clog` 類似於 `cerr` ，但完整緩衝區  
  
 從 `ostream`物件很少建構;通常使用預先定義的物件。  在某些情況下，您可以在程式啟動後重新指派預先定義的物件。  `ostream` 類別，可以為緩衝區或無緩衝區的作業設定，最適合用來執行文字模式輸出。  基底類別， `ios`中的所有功能，在 `ostream`中。  如果您建構物件類別 `ostream`，您必須指定給建構函式的 `streambuf` 物件。  
  
 `ofstream` 類別支援磁碟檔案輸出。  如果您需要一份輸出磁碟，請建構物件類別 `ofstream`。  您可以指定 `ofstream` 物件是否接受二進位或文字模式資料，在建構 `ofstream` 物件，在呼叫 `open` 成員時函式物件。  許多格式化選項和成員函式套用至 `ofstream` 物件，因此，基底類別 `ios` 和 `ostream` 的所有功能都包含在內。  
  
 如果您在建構函式中指定檔名，自動開啟該檔案，在建構物件時。  否則，您可以在叫用預設建構函式之後使用 `open` 成員函式。  
  
 與執行階段函式 `sprintf_s`， `ostringstream` 類別支援輸出至記憶體資料。  使用 I\/O 資料流格式化，若要建立記憶體中的資料，請建構物件類別 `ostringstream`。  
  
## 本章節內容  
 [建構輸出資料流物件](../standard-library/constructing-output-stream-objects.md)  
  
 [使用插入運算子和控制格式](../standard-library/using-insertion-operators-and-controlling-format.md)  
  
 [輸出檔資料流成員函式](../standard-library/output-file-stream-member-functions.md)  
  
 [緩衝的效果](../standard-library/effects-of-buffering.md)  
  
 [二進位輸出檔案](../standard-library/binary-output-files.md)  
  
 [為您的自訂類別多載 \<\< 運算子](../standard-library/overloading-the-output-operator-for-your-own-classes.md)  
  
 [撰寫不含引數的操作工具](../standard-library/writing-your-own-manipulators-without-arguments.md)  
  
## 請參閱  
 [\<ostream\> Members](http://msdn.microsoft.com/zh-tw/a5afd034-0e3c-41ee-bbd7-468d9188da1d)   
 [ofstream](../Topic/ofstream.md)   
 [ostringstream](../Topic/ostringstream.md)   
 [basic\_ostream Members](http://msdn.microsoft.com/zh-tw/82e5cc91-7c0c-4950-a8ce-ac779cfbbd93)   
 [iostream 程式設計](../standard-library/iostream-programming.md)