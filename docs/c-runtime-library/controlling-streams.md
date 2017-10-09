---
title: "控制資料流 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Controlling Streams
dev_langs:
- C++
helpviewer_keywords:
- streams, controlling
- controlling streams
- streams
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: d2211a2a2bb5121921928166626d726db8dea67f
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="controlling-streams"></a>控制資料流
[fopen](../c-runtime-library/reference/fopen-wfopen.md) 會傳回類型為 `FILE` 之物件的位址。 您可以使用此位址作為數個程式庫函式的 `stream` 引數，以在開啟檔案上執行各種作業。 針對位元組資料流，所有輸入發生的情況都會有如每個字元是透過呼叫 [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md) 的方式讀取，且所有輸出發生的情況都會有如每個字元是透過呼叫 [fputc](../c-runtime-library/reference/fputc-fputwc.md) 的方式寫入。 針對寬資料流，所有輸入發生的情況都會有如每個字元是透過呼叫 [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md) 的方式讀取，且所有輸出發生的情況都會有如每個字元是透過呼叫 [fputwc](../c-runtime-library/reference/fputc-fputwc.md) 的方式寫入。  
  
 您可以透過呼叫 [fclose](../c-runtime-library/reference/fclose-fcloseall.md) 來關閉檔案，在那之後 `FILE` 物件的位址將會無效。  
  
 `FILE` 物件會儲存資料流的狀態，包括：  
  
-   由遇到讀取或寫入錯誤的函式設為非零的錯誤指標。  
  
-   由在讀取時遇到檔案結尾的函式設為非零的檔案結尾指標。  
  
-   在檔案可以支援位置要求的情況下，指定資料流中要讀取或寫入之下一個位元組的檔案位置指標。  
  
-   [資料流狀態](../c-runtime-library/stream-states.md)能指定資料流是否會接受讀取和/或寫入，以及資料流是未繫結、位元組導向，或是寬導向。  
  
-   轉換狀態會記得所有已部分組合或產生的一般化多位元組字元的狀態，以及檔案內字元組序列的所有移位狀態。  
  
-   檔案緩衝區會指定程式庫函式可用來改善資料流讀取和寫入作業效能的陣列物件位址和大小。  
  
 請不要變更儲存在 `FILE` 物件中，或是您指定搭配該物件使用之檔案緩衝區中的任何值。 您不能複製 `FILE` 物件，並改為使用該複本的位址作為針對程式庫函式的 `stream` 引數。  
  
## <a name="see-also"></a>另請參閱  
 [檔案和資料流](../c-runtime-library/files-and-streams.md)
