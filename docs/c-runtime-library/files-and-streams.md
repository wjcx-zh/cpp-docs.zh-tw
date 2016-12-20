---
title: "檔案和資料流 | Microsoft Docs"
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
  - "檔案 [C++]"
  - "資料流"
ms.assetid: f61e712b-eac9-4c28-bb18-97c3786ef387
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 檔案和資料流
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

程式透過讀取和寫入檔案與目標環境溝通。  檔案可以是：  
  
-   您可以重複讀取和寫入資料集。  
  
-   程式所產生的位元組資料流 \(例如管線\)。  
  
-   位元組資料流接收或傳送週邊裝置。  
  
 前兩個項目是互動式檔案。  檔案通常是與程式互動的主要方式。  您可以用相同的方式操作這些檔案—透過呼叫文件庫函式。  您可以包含標準標頭 STDIO.H 以宣告這些大多的函式。  
  
 在您在檔案上執行多個作業之前，必須開啟檔案。  開啟檔案並將其與資料流，還有帶有許多不同類型檔案的標準C文件庫的資料結構做連結。  程式庫維護每一個資料流物件的型別檔案的物件。  
  
 目標環境在程式啟動前開啟三個檔案。  您也可以使用兩個引數的程式庫函式[fopen、\_wfopen](../c-runtime-library/reference/fopen-wfopen.md)開啟檔案 。\( `fopen` 函式已被取代，請改用 [fopen\_s、\_wfopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) \)。第一個引數是檔名。  第二個引數是指定的 C\+\+. 字串:  
  
-   您是否想要讀取資料從檔案或將它或兩個寫入資料。  
  
-   您是否想要產生檔案的新內容 \(或建立檔案，如果先前尚未存在\) 或保留現有內容之後。  
  
-   對檔案進行寫入是否修改現有內容或應該只附加位元組位於檔案結尾。  
  
-   您要操作文字資料流或二進位資料流。  
  
 只要順利開啟檔案，您變可以判斷資料流是否支援字元組 \(位元組資料流\) 或寬度放置 \(寬資料流\)。  資料流最初是無界的。  在決定其他函式時使其方向的寬度時，呼叫某些函式在資料流使其面向位元組。  一旦建立之後，資料流會維護其本身的方向，直到由 [fclose](../c-runtime-library/reference/fclose-fcloseall.md) 或 [freopen](../c-runtime-library/reference/freopen-wfreopen.md)的呼叫關閉。  
  
 P.J. 的© 1989\-2001。  Plauger 和 Jim Brodie。  著作權所有，並保留一切權利。  
  
## 請參閱  
 [文字和二進位資料流](../c-runtime-library/text-and-binary-streams.md)   
 [位元組和寬資料流](../c-runtime-library/byte-and-wide-streams.md)   
 [控制資料流](../c-runtime-library/controlling-streams.md)   
 [資料流狀態](../c-runtime-library/stream-states.md)