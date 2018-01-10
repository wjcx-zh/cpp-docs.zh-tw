---
title: "Windows Sockets： 使用封存的通訊端範例 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0e70e8ecc14496b03bc758d91f078a926f33532
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets：使用封存的通訊端範例
本文件提供使用類別的範例[CSocket](../mfc/reference/csocket-class.md)。 此範例會採用`CArchive`序列化資料，透過通訊端的物件。 請注意，這不是文件序列化或檔案。  
  
 下列範例說明您如何使用封存來傳送和接收資料透過`CSocket`物件。 此範例的設計，讓兩個執行個體 （在相同電腦上或在網路上的不同電腦上） 的應用程式交換資料。 一個執行個體傳送資料，而另一個執行個體接收和認可。 其中一個應用程式可以初始化交換，而且是可做為伺服器或另一個應用程式的用戶端。 下列函式定義在應用程式的檢視類別中：  
  
 [!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]  
  
 有關這個範例的最重要的一點是它的結構與 MFC 的`Serialize`函式。 **PacketSerialize**成員函式組成**如果**陳述式搭配**else**子句。 此函式會接收兩個[CArchive](../mfc/reference/carchive-class.md)做為參數的參考：`arData`和`arAck`。 如果`arData`封存物件設定為儲存 （傳送）**如果**分支便會執行; 否則如果`arData`設定載入 （接收） 此函數會採用**else**分支。 如需在 MFC 中序列化的詳細資訊，請參閱[序列化](../mfc/how-to-make-a-type-safe-collection.md)。  
  
> [!NOTE]
>  `arAck`封存物件會被假設為相反`arData`。 如果`arData`是傳送，`arAck`接收，而且反之則不然，則為 true。  
  
 進行傳送，範例函式執行迴圈的次數，每次產生一些隨機資料供示範之用的指定數目。 您的應用程式會取得實際資料從某個來源，例如檔案。 `arData`封存的插入運算子 (**<<**) 用來傳送的資料流，三個連續的資料區塊：  
  
-   「 標頭 」，指定資料的本質 (在此情況下，值`bValue`變數，並且將傳送多少個複本)。  
  
     這兩個項目會隨機產生的這個範例。  
  
-   指定的資料複本數目。  
  
     內部**如**迴圈傳送`bValue`指定的次數。  
  
-   字串呼叫`strText`收件者要顯示給使用者。  
  
 用於接收，此函數操作同樣地，不同之處在於它會使用封存的引出運算子 (**>>**) 取得從封存的資料。 接收應用程式會驗證它接收的資料，會顯示最後的 「 接收 」 訊息，然後送回訊息，指出 「 已傳送 」 顯示傳送應用程式。  
  
 在此通訊模型中，「 接收 」 這個字，訊息傳送`strText`變數，並不是位於另一端的通訊，因此它會指定要接收使用者確認收到資料封包數目。 接收者會以類似的字串，指出原始傳送者的螢幕上的 「 傳送 」，以便顯示回覆。 兩個字串的回條表示已發生成功進行通訊。  
  
> [!CAUTION]
>  如果您要撰寫 MFC 用戶端程式與所建立的 (非 MFC) 伺服器進行通訊，請不要透過封存傳送 C++ 物件。 除非伺服器是 MFC 應用程式以了解您想要傳送的物件類型，否則將無法接收和還原序列化物件。 本文範例[Windows Sockets： 位元組順序](../mfc/windows-sockets-byte-ordering.md)顯示此類型的通訊。  
  
 如需詳細資訊，請參閱 Windows Sockets 規格： **htonl**， **htons**， **ntohl**， **ntohs**。 此外，如需詳細資訊，請參閱：  
  
-   [Windows Sockets：從通訊端類別衍生](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets：如何搭配使用通訊端與封存](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets：背景](../mfc/windows-sockets-background.md)  
  
## <a name="see-also"></a>請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)   
 [CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)   
 [CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)   
 [CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)   
 [CArchive::Flush](../mfc/reference/carchive-class.md#flush)   
 [Cobject:: Serialize](../mfc/reference/cobject-class.md#serialize)

