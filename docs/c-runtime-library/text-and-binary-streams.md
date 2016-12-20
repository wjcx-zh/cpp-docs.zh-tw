---
title: "文字和二進位資料流 | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "二進位資料流"
  - "文字資料流"
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 文字和二進位資料流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文字資料流包括可寫入文字導向顯示撰寫的一或多行文字，以便讀取。  當讀取文字資料流時，程式在每行結尾讀取 `NL` \(新行\)。  當寫入文字資料流時，程式將以 `NL` 表示行尾。  要符合目標環境中的不同的慣例所表示之檔案中的文字，程式庫函式可以修改字元數和表示傳輸程式和文字資料流之間。  
  
 因此，放置在文字資料流中會有所限制。  您可以藉由呼叫 [fgetpos](../c-runtime-library/reference/fgetpos.md) 或 [ftell](../c-runtime-library/reference/ftell-ftelli64.md)取得目前檔案位置指示器。  您可以藉由呼叫 [fsetpos](../c-runtime-library/reference/fsetpos.md) 或 [fseek](../c-runtime-library/reference/fseek-fseeki64.md)以將文字資料流中放置在取得的位置或是開頭或結尾。  其他位置的變更將不會不支援。  
  
 對於最大可攜性，程式不應該寫入:  
  
-   空檔案。  
  
-   空白字元在一行的結尾。  
  
-   部分涵蓋行 \(透過省略 `NL` 在檔案結尾\)。  
  
-   除了可列印的字元、NL 和 `HT` \(水平索引標籤\) 以外的字元。  
  
 如果您遵循這些規則，則會在您建立檔案時，將文字資料流讀取字元的序列 \(在位元組或多位元組字元\) 會比對字元序列您寫入文字資料流。  否則，當您關閉時，如果檔案是空的，則程式庫函式可以刪除您所建立的檔案。  也可以修改或刪除您寫入檔案的字元。  
  
 二進位資料流包含一個或多個位元組的選擇性資訊。  當您撰寫它時，您可以撰寫在對物件 \(位元組\) 的二進位資料流的任意物件儲存的值和正確地讀取什麼是儲存在物件中。  程式庫函式不會修改傳輸程式和二進位資料流之間的位元組。  不過它們可以附加任意數目的位元組到您寫入二進位資料流的檔案。  程式必須處理這些額外的空間位元組在所有二進位資料流結尾。  
  
 因此，除了資料流末端的置放，置放在二進位資料流中是明確定義的。  您可以取得及修改目前檔案位置指示器相同文字資料流。  此外，位移使用 [ftell](../c-runtime-library/reference/ftell-ftelli64.md) and [fseek](../c-runtime-library/reference/fseek-fseeki64.md) 計算最初資料流\(位元組是零\)，所以在這些位移的整數算術產生可預測的結果。  
  
 位元組資料流將檔案當做位元組序列。  在程式中，資料流看起來像位元組順序相同，除了所描述的可能變更上面。  
  
## 請參閱  
 [檔案和資料流](../c-runtime-library/files-and-streams.md)