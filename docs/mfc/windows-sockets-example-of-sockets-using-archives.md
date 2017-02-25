---
title: "Windows Sockets：使用封存的通訊端範例 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "範例 [MFC], Windows Sockets"
  - "通訊端 [C++], 與封存"
  - "Windows Sockets [C++], 與封存"
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Windows Sockets：使用封存的通訊端範例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將使用類別的範例 [CSocket](../mfc/reference/csocket-class.md)。  這個範例會使用 `CArchive` 物件的通訊端序列化資料。  請注意這不是文件序列化至檔案。  
  
 下列範例說明如何使用封存透過 `CSocket` 物件所傳送和接收資料。  範例設計，讓應用程式 \(在相同的電腦上或在網路上的不同電腦\) 交換資料的兩個執行個體。  執行個體傳送資料，另一個執行個體中的通知。  任一應用程式可以啟始切換，因此將可當做伺服器或用戶端到另一個應用程式。  下列函式在應用程式的檢視類別定義:  
  
 [!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/CPP/windows-sockets-example-of-sockets-using-archives_1.cpp)]  
  
 如需這個範例的最重要的事是 MFC `Serialize` 函式其結構平行。  **PacketSerialize** 成員函式包括與 **else** 子句的 **if** 陳述式。  函式會接收兩個 [CArchive](../mfc/reference/carchive-class.md) 參考做為參數: `arData` 和 `arAck`。  如果 `arData` 封存物件為儲存 \(傳送\) 設定， **if** 分支執行;否則，則為，如果 `arData` 為載入 \(接收\) 設定函式採用 **else** 分支。  如需如何以 MFC 撰寫序列化的詳細資訊，請參閱[序列化](../mfc/how-to-make-a-type-safe-collection.md)。  
  
> [!NOTE]
>  `arAck` 封存物件假設 `arData`是相反。  如果 `arData` 是要傳送 `arAck` 接收，計數器為 true。  
  
 對於傳送，範例函式為迴圈時，都會產生一些隨機資料的指定次數為了便於示範。  您的應用程式將衍生自某個來源的實際資料，例如檔案。  `arData` 表示檔案的插入運算子 \(**\<\<**\) 用於傳送資料的連續區塊資料流:  
  
-   指定資料的性質的標題 \(在此例中， `bValue` 變數的值，以及可供傳送\)。  
  
     兩個項目對於這個範例會隨機產生。  
  
-   指定之資料的複本數目。  
  
     內部 **for** 重複傳送 `bValue` 指定的次數。  
  
-   字串呼叫接收者顯示給使用者的 `strText` 。  
  
 對於接收函式，功能差不多，但是從封存中使用捲軸的檔案擷取運算子 \(**\>\>**\) 取得資料。  接收應用程式驗證資料，最後顯示「接收訊息」，然後傳回稱為「傳送」的傳回顯示訊息。  
  
 在這個中通訊模型， 「接收」的文字，在 `strText` 變數所傳送的訊息，是顯示在通訊的另一端，因此，指定給接收使用者的一些資料包接收。  接收者回覆與稱為「傳送」的相同的字串，在原始寄件者的螢幕顯示的。  開啟收款兩個字串表示成功的通訊時發生。  
  
> [!CAUTION]
>  如果您正在撰寫一個 MFC 用戶端程式建立的 \(非 MFC\) 伺服器通訊，請勿將封存傳送 C\+\+ 物件。  除非伺服器是了解這種物件的 MFC 應用程式要傳送，無法接收和序列化您的物件。  一個範例會在 [Windows Sockets:位元組順序](../mfc/windows-sockets-byte-ordering.md) 一文顯示型別的通訊。  
  
 如需詳細資訊，請參閱 Windows Sockets 規格: **htonl**， **ntohl**， **ntohl**， **ntohs**。  如需詳細資訊，請參閱:  
  
-   [Windows Sockets：從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets：背景](../mfc/windows-sockets-background.md)  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)   
 [CArchive::IsStoring](../Topic/CArchive::IsStoring.md)   
 [CArchive::operator \<\<](../Topic/CArchive::operator%20%3C%3C.md)   
 [CArchive::operator \>\>](../Topic/CArchive::operator%20%3E%3E.md)   
 [CArchive::Flush](../Topic/CArchive::Flush.md)   
 [CObject::Serialize](../Topic/CObject::Serialize.md)