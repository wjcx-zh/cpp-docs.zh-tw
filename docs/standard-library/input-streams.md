---
title: "輸入資料流 | Microsoft Docs"
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
  - "資料 [C++], 從輸入資料流讀取"
  - "輸入資料流物件"
  - "輸入資料流"
  - "讀取資料 [C++], 從輸入資料流"
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
caps.latest.revision: 11
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 輸入資料流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

輸入資料流物件是位元組來源。  三個最重要的輸入資料流類別是 [istream](http://msdn.microsoft.com/zh-tw/6801779e-260e-416d-b4ec-fef5ff1b2371)、 [ifstream](../Topic/ifstream.md)和 [istringstream](../Topic/istringstream.md)。  
  
 `istream` 類別最適合用於執行文字模式項目使用。  您可以設定類別 `istream` 物件緩衝區或無緩衝區的作業。  基底類別， `ios`中的所有功能，在 `istream`中。  您很少會從類別建構 `istream`的物件。  相反地，您通常會使用預先定義的 `cin` 物件，實際上是類別 [ostream](../standard-library/ostream.md)物件。  在某些情況下，您可以將 `cin` 加入至其他資料流物件在程式啟動後。  
  
 `ifstream` 類別支援磁碟檔案項目。  如果您需要輸入磁碟檔案，請建構物件類別 `ifstream`。  您可以指定二進位或文字模式的資料。  如果您在建構函式中指定檔名，自動開啟檔案，在建構物件時。  否則，您可以在叫用預設建構函式會使用 `open` 函式。  許多格式化選項和成員函式套用至 `ifstream` 物件。  基底類別 `ios` 和 `istream` 的所有功能在 `ifstream`中。  
  
 像程式庫函式 `sscanf_s`， `istringstream` 類別支援從記憶體中字串的項目。  從有 null 結束字元的字元陣列要擷取資料，請配置並初始化字串，然後建構物件類別 `istringstream`。  
  
## 本章節內容  
 [建構輸入資料流物件](../standard-library/constructing-input-stream-objects.md)  
  
 [使用擷取運算子](../standard-library/using-extraction-operators.md)  
  
 [測試是否有擷取錯誤](../standard-library/testing-for-extraction-errors.md)  
  
 [輸入資料流操作工具](../standard-library/input-stream-manipulators.md)  
  
 [輸入資料流成員函式](../standard-library/input-stream-member-functions.md)  
  
 [為您的自訂類別多載 \>\> 運算子](../standard-library/overloading-the-input-operator-for-your-own-classes.md)  
  
## 請參閱  
 [iostream 程式設計](../standard-library/iostream-programming.md)