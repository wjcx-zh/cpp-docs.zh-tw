---
title: "位元組和寬資料流 | Microsoft Docs"
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
  - "Byte and Wide Streams"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "位元組資料流"
  - "寬資料流"
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 位元組和寬資料流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

位元組資料流將檔案當做位元組序列。  在程式中，資料流與位元組序列完全相同。  
  
 相反地，寬資料流視為檔案做為通用多位元組字元序列，可能有各種編碼規則。\(文字和二進位檔案仍然讀取和如前所述寫入\)。在程式中，資料流看起來像寬字元對應的序列。  在兩個表示之間轉換在標準 C 程式庫內發生。  轉換規則原則上會因呼叫修改`LC_CTYPE`類別的[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)而有所修改。  每個寬資料流在它成為寬度放置時判斷它的轉換規則，並保留這些規則，即使 `LC_CTYPE` 分類之後變更。  
  
 一個寬資料流內的位置與文字資料流的限制相同。  而且，檔案位置指示器會確定必須處理狀態相關的程式碼。  一般而言，它包含在資料流和`mbstate_t`的物件中的位元組位移。  因此，取得寬資料流中的檔案位置唯一可靠的方式是藉由呼叫 [fgetpos](../c-runtime-library/reference/fgetpos.md)，而唯一可靠的還原衍生的位置的方式是藉由元件呼叫 [fsetpos](../c-runtime-library/reference/fsetpos.md)。  
  
## 請參閱  
 [檔案和資料流](../c-runtime-library/files-and-streams.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)