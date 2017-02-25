---
title: "Windows Sockets：位元組順序 | Microsoft Docs"
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
  - "通訊端程式設計中的位元組順序問題"
  - "通訊端 [C++], 位元組順序問題"
  - "Windows Sockets [C++], 位元組順序問題"
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows Sockets：位元組順序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文和兩個方針手冊說明視窗通訊端程式設計的幾個問題。  本文包含位元組順序。  其他問題的文章報表: [Windows Sockets:封鎖](../mfc/windows-sockets-blocking.md) 和 [Windows Sockets:將字串轉換](../mfc/windows-sockets-converting-strings.md)。  
  
 如果您從 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)類別使用或衍生自類別，您必須處理這些問題。  如果您從 [CSocket](../mfc/reference/csocket-class.md)類別使用或衍生， MFC 會為您處理它們。  
  
## 位元組順序  
 不同機器架構有時候使用不同位元組順序存放資料。  例如，在 Macintosh \(Motorola\) 機器相反順序 Intel 架構電腦存放區資料。  Intel 位元組順序，稱為位元組由小到大，」也是 Web 標準「位元組由大到小順序的相反。  下表說明這些詞彙。  
  
### 由大到小與由小到大的位元組順序  
  
|位元組順序|意義|  
|-----------|--------|  
|位元組由大到小|表示最大顯著性位元組位於文字左端。|  
|位元組由小到大|表示最大顯著性位元組位於文字右端。|  
  
 通常，您不必擔心您在網路上傳送和接收資料的位元組順序轉換，不過，您必須將位元組順序的情況。  
  
## 當您必須轉換成位元組順序。  
 您需要在下列情況下將位元組順序:  
  
-   您將需要透過網路說明的資訊，與您傳送到另一部電腦的資料\)。  例如，您可以透過通訊埠和網路位址，必須了解。  
  
-   您進行通訊的伺服器應用程式不是 MFC 應用程式 \(以及您沒有原始程式碼\)。  這個呼叫的位元組順序轉換，如果兩部機器不共用相同的位元組順序。  
  
## 當您不需要將位元組順序  
 您可以避免在下列情況下將位元組順序工作:  
  
-   在兩端的電腦可能不同意交換位元組，，且兩個電腦使用相同的位元組順序。  
  
-   您通訊的伺服器是 MFC 應用程式。  
  
-   您通訊之伺服器上的原始程式碼，因此，您可以明確地指出是否必須將位元組順序。  
  
-   您可以將伺服器加入至 MFC。  這很容易進行，因此，結果通常較小，更快速的程式碼。  
  
 使用 [CAsyncSocket](../mfc/reference/casyncsocket-class.md)，您必須處理所有必要的位元組順序轉換。  Windows Sockets 標準化「位元組由大到小位元組順序模型並提供函式可在此順序和其他之間轉換。  [CArchive](../mfc/reference/carchive-class.md)，不過，可以使用 [CSocket](../mfc/reference/csocket-class.md)，使用此相反 \(位元組由小到大順序\)，不過， `CArchive` 會處理位元組順序轉換您的詳細資料。  您可以在應用程式中使用此標準順序或使用 Windows Sockets 位元組順序轉換函式，您可以讓程式碼更具有可攜性。  
  
 使用 MFC 通訊端的理想情況是當您在撰寫兩端通訊:在兩端使用 MFC。  如果您正在撰寫與非 MFC 應用程式將通訊，例如 FTP 伺服器，您的應用程式可能需要處理位元組交換使用 Windows Sockets 轉換常式 **ntohs**和 **ntohl**和 **htons**和 **htonl**之前，在中，在您將資料傳遞至封存物件。  用於通訊的這些函式的範例與非 MFC 應用程式本文後面。  
  
> [!NOTE]
>  當通訊的另一端非 MFC 應用程式時，您也必須避免資料流從 `CObject` 取得的 C\+\+ 物件到封存，因為接收者無法處理它們。  請參閱 [Windows Sockets:使用已封存的通訊端](../mfc/windows-sockets-using-sockets-with-archives.md)中的注意事項。  
  
 如需位元組順序的詳細資訊，請參閱 Windows Sockets 規格，在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中使用。  
  
## 位元組順序轉換範例  
 下列範例顯示使用封存之 `CSocket` 物件的序列化函式。  使用在 Windows Sockets API，的位元組順序轉換函式同時說明。  
  
 這個範例中呈現您撰寫用戶端與非 MFC 伺服器應用程式通訊。您無法存取原始程式碼的情節。  在這個案例中，您必須假設，非 MFC 伺服器使用標準網路位元組順序。  相反地，您的 MFC 用戶端應用程式使用與 `CSocket` 物件的 `CArchive` 物件和 `CArchive` 會使用位元組由小到大的位元組順序， Web 標準的相反。  
  
 假設您計劃通訊有訊息封包中建立的通訊協定如下的非 MFC 伺服器:  
  
 [!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/CPP/windows-sockets-byte-ordering_1.cpp)]  
  
 以 MFC 來說，這表示如下:  
  
 [!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/CPP/windows-sockets-byte-ordering_2.cpp)]  
  
 在 C\+\+ 中， `struct` 基本上是項目與類別相同。  `Message` 結構可以具有成員函式，例如宣告的 `Serialize` 成員函式以上。  `Serialize` 成員函式如下所示::  
  
 [!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/CPP/windows-sockets-byte-ordering_3.cpp)]  
  
 這個範例會要求資料位元組順序轉換，因為有非 MFC 伺服器應用程式的位元組順序在一端和用於在另一端的 MFC 用戶端應用程式的 `CArchive` 之間沒有清楚的不符。  範例說明數個位元組順序轉換函式 Windows Sockets 提供。  下表將說明這些函式。  
  
### Windows Sockets 位元組順序轉換函式  
  
|功能|用途|  
|--------|--------|  
|**ntohs**|轉換從網路位元組順序轉換為 16 位元的個數的位元組順序 \(位元組由小到大的位元組由大到小\)。|  
|**ntohl**|轉換從網路位元組順序轉換為 32 位元的個數的位元組順序 \(位元組由小到大的位元組由大到小\)。|  
|**Htons**|轉換從主機位元組順序轉換為 16 位元的網路位元組順序 \(位元組由小到大的位元組由大到小\)。|  
|**Htonl**|轉換從主機位元組順序轉換為 32 位元的網路位元組順序 \(位元組由小到大的位元組由大到小\)。|  
  
 這個範例另一點是，在另一端通訊的通訊端應用程式為非 MFC 應用程式時，您必須避免建立類似下列:  
  
 `ar << pMsg;`  
  
 其中 `pMsg` 是指向衍生自類別的 C \+\+. `CObject`物件。  這會傳送額外 MFC 資訊與物件，以及伺服器不了解，，它會，如果它是 MFC 應用程式。  
  
 如需詳細資訊，請參閱：  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：背景](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)