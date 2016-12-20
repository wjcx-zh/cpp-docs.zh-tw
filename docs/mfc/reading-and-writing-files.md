---
title: "讀取和寫入檔案 | Microsoft Docs"
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
  - "CFile 類別, 物件"
  - "CFile 類別, 讀取和寫入 CFile 物件"
  - "範例 [MFC], 讀取檔案"
  - "範例 [MFC], 寫入檔案"
  - "檔案 [C++], 讀取"
  - "檔案 [C++], 寫入至"
  - "MFC [C++], 檔案作業"
  - "讀取檔案"
  - "寫入檔案 [C++]"
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 讀取和寫入檔案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您使用了 C 執行階段程式庫檔案處理函式，讀取和寫入作業的 MFC 將會熟悉。  本文說明直接從讀取和寫入直接寫入 `CFile` 物件。  您也可以使用 [CArchive](../mfc/reference/carchive-class.md) 類別的緩衝區的檔案 I\/O。  
  
#### 讀取和寫入檔案  
  
1.  使用 **Read** 和 **Write** 成員函式讀取和寫入資料的檔案。  
  
     \-或\-  
  
2.  `Seek` 的成員函式移動也可移至檔案內的指定位移。  
  
 **Read** 接受指標到緩衝區的位元組數目讀取並傳回讀取的實際位元組數目。  如果所需的位元組數無法讀取，因為檔案結尾 \(EOF\) 為止，讀取的實際位元組數目。  如果任何讀取錯誤發生，就會擲回例外狀況。  **Write** 類似 **Read**，不過，寫入的位元組數目不會傳回。  如果寫入錯誤，包括不寫入指定的所有位元組，就會擲回例外狀況。  如果您有一個有效的 `CFile` 物件，如下列範例所示，您可以讀取或寫入:  
  
 [!code-cpp[NVC_MFCFiles#2](../mfc/codesnippet/CPP/reading-and-writing-files_1.cpp)]  
  
> [!NOTE]
>  您通常應該執行 **try**和**catch** 例外狀況處理區塊內的輸入\/輸出作業。  如需詳細資訊，請參閱 [例外狀況處理 \(MFC\)](../mfc/exception-handling-in-mfc.md)。  
  
## 請參閱  
 [檔案](../mfc/files-in-mfc.md)