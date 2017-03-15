---
title: "控制資料流 | Microsoft Docs"
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
  - "Controlling Streams"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "控制資料流"
  - "資料流"
  - "資料流, 控制"
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 控制資料流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[fopen](../c-runtime-library/reference/fopen-wfopen.md) 傳回型別為 `FILE`之物件的位址。  您可以使用這個位址做為 `stream` 引數套用至多個程式庫函式會在開啟檔案的各種作業。  對於位元組資料流，所有輸入發生，就像是每個字元會藉由呼叫 [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md)讀取，因此，所有輸出結果，就像是每個字元會藉由呼叫 [fputc](../c-runtime-library/reference/fputc-fputwc.md)寫入。  對於位元組資料流，所有輸入發生，就像是每個字元會藉由呼叫 [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md)讀取，因此，所有輸出結果，就像是每個字元會藉由呼叫 [fputc](../c-runtime-library/reference/fputc-fputwc.md)寫入。  
  
 您可以藉由呼叫 [fclose](../c-runtime-library/reference/fclose-fcloseall.md)關閉檔案中，之後， `FILE` 物件的位址無效。  
  
 `FILE` 物件所儲存之資料流的狀態，包括：  
  
-   錯誤指示器集合遇到非零會造成讀取或寫入錯誤的函式。  
  
-   檔案結尾標記由函式設定為非零，該函式在讀取時遇到檔案結尾。  
  
-   如果檔案可能支援當地語系化的需求，檔案位置指示器在資料流的下一個位元組讀取或寫入。  
  
-   [資料流狀態](../c-runtime-library/stream-states.md) 指定資料流是否會接受讀取及\/或寫入，且資料流是否未繫結，以及一個雙位元組的或寬度放置。  
  
-   轉換狀態記住任何部分已安裝或產生的通用多位元組字元狀態，以及其中任一個將位元組序列的狀態在檔案中\)。  
  
-   檔案緩衝區指定陣列物件位址和大小程式庫函式可以使用以改善效能、讀取和寫入資料流寫入作業。  
  
 請您不要更改任何儲存在 `FILE` 物件或儲存在您為使用者指定的檔案緩衝器物件的值。  您無法複製 `FILE` 物件，並且 portably 使用複製的位址為 `stream` 引數對程式庫函式。  
  
## 請參閱  
 [檔案和資料流](../c-runtime-library/files-and-streams.md)