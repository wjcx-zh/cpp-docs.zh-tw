---
title: "檔案和資料流 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- files [C++]
- streams
ms.assetid: f61e712b-eac9-4c28-bb18-97c3786ef387
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0285d8395b5a135ac75c40914232ad820f36f00
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="files-and-streams"></a>檔案和資料流
透過讀取和寫入檔案，以便與目標環境溝通的程式。 檔案可以是：  
  
-   可以重複讀取與寫入的資料集。  
  
-   程式所產生的位元組資料流 (例如管線)。  
  
-   接收自或傳送到週邊裝置的位元組資料流。  
  
 最後兩個項目是互動式的檔案。 檔案通常是用來與程式互動的主要方式。 所有這類檔案的管理都方式非常類似，亦即呼叫程式庫函式。 包含標準標頭 STDIO.H，即可宣告大部分的這些函式。  
  
 針對檔案執行眾多作業之前，必須先開啟檔案。 開啟檔案會將檔案與資料流產生關連。資料流是標準 C 程式庫內的資料結構，可以掩蓋各種檔案之間的許多差異。 程式庫會在類型 FILE 的物件中維護每個資料流的狀態。  
  
 目標環境會在程式啟動前開啟三個檔案。 您可以使用兩個引數來呼叫程式庫函式 [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)，以開啟檔案。 (`fopen` 函式已淘汰，請改用 [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md))。第一個引數是檔案名稱。 第二個引數是指定下列事項的 C 字串：  
  
-   是否要從檔案讀取資料，或要將資料寫入檔案，或是兩者皆要。  
  
-   是否要產生新的檔案內容 (或者如果原本沒有檔案，則建立檔案)，或將現有的內容保留不動。  
  
-   寫入檔案時是否可以修改現有的內容，或僅會在檔案結尾處附加位元組。  
  
-   是否要操作文字資料流或二進位資料流。  
  
 順利開啟檔案後，接著要決定資料流是位元組導向 (位元組資料流) 還是寬字元導向 (寬資料流)。 資料流一開始的時候並未繫結。 呼叫某些特定函式在資料流上執行作業，會讓資料流變成位元組導向，而某些特定函式則會讓資料流變成寬字元導向。 一旦決定資料流的位元組導向或寬字元導向之後，便維持不變，直到呼叫 [fclose](../c-runtime-library/reference/fclose-fcloseall.md) 或 [freopen](../c-runtime-library/reference/freopen-wfreopen.md) 將資料流關閉為止。  
  
 © 1989-2001 P.J. Plauger 與 Jim Brodie 著。 著作權所有，並保留一切權利。  
  
## <a name="see-also"></a>請參閱  
 [文字和二進位資料流](../c-runtime-library/text-and-binary-streams.md)   
 [位元組和寬資料流](../c-runtime-library/byte-and-wide-streams.md)   
 [控制資料流](../c-runtime-library/controlling-streams.md)   
 [資料流狀態](../c-runtime-library/stream-states.md)