---
title: "Windows Sockets：如何搭配使用通訊端與封存 | Microsoft Docs"
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
  - "通訊端 [C++], 同步作業"
  - "通訊端 [C++], 與封存"
  - "同步狀態通訊端"
  - "兩狀態通訊端物件"
  - "Windows Sockets [C++], 同步"
  - "Windows Sockets [C++], 與封存"
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets：如何搭配使用通訊端與封存
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明 [CSocket](../mfc/reference/csocket-class.md) 物件、 [CSocketFile](../mfc/reference/csocketfile-class.md) 物件和 [CArchive](../mfc/reference/carchive-class.md) 物件如何合併透過 Windows Sockets 簡化傳送和接收資料。  
  
 這篇文章 [Windows Sockets:通訊端的範例使用封存的](../mfc/windows-sockets-example-of-sockets-using-archives.md) 提出 **PacketSerialize** 函式。  在 **PacketSerialize** 範例工作的封存物件很像封存物件傳遞至 MFC [序列化](../Topic/CObject::Serialize.md) 函式。  主要的差異在於，通訊端的封存不附加至標準的 [C 檔案](../mfc/reference/cfile-class.md) 物件 \(通常是與磁碟檔案\)，但是對 `CSocketFile` 物件。  而不是連接到磁碟檔案， `CSocketFile` 物件連接到 `CSocket` 物件。  
  
 `CArchive` 物件會管理緩衝區。  當一儲存 \(傳送的\) 封存的緩衝區已滿，關聯的 `CFile` 物件寫入輸出緩衝區的內容。  清除封存的緩衝區附加至通訊端與傳送訊息\)。  當載入 \(sInk\) 時封存的緩衝區已滿， `CFile` 物件停止讀取，直到緩衝區已無法使用。  
  
 `CSocketFile` 類別，衍生自 `CFile`，但不支援 [C 檔案](../mfc/reference/cfile-class.md) 成員函式來定位功能 \(`Seek`、 `GetLength`， `SetLength`，等等\)，鎖定函式 \(`LockRange`， `UnlockRange`\)，或者 `GetPosition` 函式。  所有 [CSocketFile](../mfc/reference/csocketfile-class.md) 物件必須將寫入或讀取位元組序列相互關聯的 `CSocket` 物件。  由於檔案不是包含的作業，例如 `Seek` 和 `GetPosition` 沒有意義。  `CSocketFile` ，衍生自 `CFile`，所以通常會繼承這些成員函式。  若要防止這種情況，不支援的 `CFile` 成員函式在 `CSocketFile` 覆寫會擲回 [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)。  
  
 其 `CSocket` 的 `CSocketFile` 物件呼叫成員函式會傳送或接收資料。  
  
 下圖顯示在這些物件之間的關聯性在通訊的兩側。  
  
 ![CArchive、CSocketFile 和 CSocket](../mfc/media/vc38ia1.png "vc38IA1")  
CArchive、CSocketFile 和 CSocket  
  
 這個資訊清單的複雜的目的是要保護您從處理通訊端的必要詳細。  您建立通訊端、檔案和封存，然後開始傳送或接收資料可以插入至封存或擷取它從封存。  [CArchive](../mfc/reference/carchive-class.md)、 [CSocketFile](../mfc/reference/csocketfile-class.md)和 [CSocket](../mfc/reference/csocket-class.md) 在幕後管理詳細資料。  
  
 `CSocket` 物件其實是兩種狀態的物件:有時候非同步 \(通常狀態\) 有時同步。  在它的非同步狀態，通訊端可接收架構的非同步通知。  然而，在執行作業時 \(例如接收或傳送資料的通訊變得同步。  這表示通訊端不會收到進一步非同步通知，直到這次同步作業已完成。  由於交換模式，您可以執行，例如，類似下列的資訊:  
  
 [!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/CPP/windows-sockets-how-sockets-with-archives-work_1.cpp)]  
  
 如果 `CSocket` 尚未實作為兩種狀態的物件，接收相同類型的額外的通知事件可能是可行的，當您處理上一個告知時。  例如，您可能會取得 `OnReceive` 通知，當處理 `OnReceive`時。  在上述程式碼片段，擷取 `str` 從封存可能造成遞迴。  您可以切換狀態， `CSocket` 可以防止其他通知防止遞迴。  一般規則是在通知內沒有通知。  
  
> [!NOTE]
>  檔案，而不是 `CArchive` 物件， `CSocketFile` 也可以使用，將 \(有限的\)。  根據預設， `CSocketFile` 建構函式的 `bArchiveCompatible` 參數是 **TRUE**。  這會指定檔案物件適合與封存的。  若要使用檔案物件，而不用封存，請傳入 `bArchiveCompatible` 參數的 **FALSE** 。  
  
 在其封存相容的模式下， `CSocketFile` 物件會提供更好的效能並且減少「死結的風險」。發生死結時，在傳送和接收的通訊端互相等候，或等候公用資源。  這種情況，就可能會發生 `CArchive` 物件與 `CSocketFile` 一起使用它對 `CFile` 物件的方式。  `CFile`，可以封存，假設，如果它收到較少的位元組比要求，檔案結尾結尾。  `CSocketFile`，然而，資料是以訊息;緩衝區小於要求的位元組數不表示檔案結尾可能包含多個訊息，因此，接收。  應用程式在此狀況下不會封鎖，它可以使用，則為 `CFile`，而且可以繼續讀取緩衝處理的訊息，直到緩衝區是空的。  在 `CArchive` 的 [IsBufferEmpty](../Topic/CArchive::IsBufferEmpty.md) 函式為在這種情況下監視捲軸檔案之緩衝區的狀態會很有用。  
  
 如需詳細資訊，請參閱 [Windows Sockets:使用已封存的通訊端](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)   
 [CObject::Serialize](../Topic/CObject::Serialize.md)