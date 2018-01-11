---
title: "Windows Sockets： 位元組順序 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c25a7b2c8240531e1d778d6a119f857032423db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets：位元組順序
本文和兩個方針手冊說明了 Windows Sockets 程式設計的幾個問題。 本文涵蓋位元組順序。 其他問題包含於下列文章中： [Windows Sockets： 封鎖](../mfc/windows-sockets-blocking.md)和[Windows Sockets： 轉換字串](../mfc/windows-sockets-converting-strings.md)。  
  
 如果您使用，或衍生自類別[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，您必須自行管理這些問題。 如果您使用，或衍生自類別[CSocket](../mfc/reference/csocket-class.md)，MFC 會為您管理它們。  
  
## <a name="byte-ordering"></a>位元組順序  
 不同架構有時會使用不同的位元組順序的資料儲存。 例如，intel 機器會將資料儲存在 Macintosh (Motorola) 電腦的反向順序。 Intel 位元組順序，稱為 「 由小到大，」 也是網路標準"Big-endian"順序相反。 下表說明這些詞彙。  
  
### <a name="big--and-little-endian-byte-ordering"></a>大-和位元組由小到大位元組順序  
  
|位元組順序|意義|  
|-------------------|-------------|  
|Big Endian|最大顯著性位元組位於左文字的結尾。|  
|Little Endian|最大顯著性位元組是右端的文字。|  
  
 一般而言，您不必擔心資料傳送，並透過網路接收的位元組順序轉換，但有的情況中，您必須轉換位元組順序。  
  
## <a name="when-you-must-convert-byte-orders"></a>當您必須將位元組順序的轉換  
 您必須轉換位元組順序，在下列情況：  
  
-   您要將解譯網路，而不是您要傳送給另一部電腦的資料所需的資訊。 例如，您可能會傳遞連接埠和位址，必須了解網路。  
  
-   與您通訊的伺服器應用程式不是 MFC 應用程式 （及您沒有為其原始碼）。 這會呼叫位元組順序轉換如果兩部電腦不會共用相同的位元組順序。  
  
## <a name="when-you-do-not-have-to-convert-byte-orders"></a>當您沒有轉換位元組順序  
 您可以避免轉換在下列情況中的位元組順序的工作：  
  
-   兩端機器可以接受未交換位元組，，這兩部電腦使用相同的位元組順序。  
  
-   MFC 應用程式的伺服器的後方。  
  
-   您有原始程式碼伺服器正在通訊，因此您可以分辨明確是否與否，您必須轉換位元組順序。  
  
-   您可以移植到 MFC 伺服器。 這是相當容易，，結果通常是較小、 更快速的程式碼。  
  
 使用[CAsyncSocket](../mfc/reference/casyncsocket-class.md)，您必須自行管理任何所需的位元組順序的轉換。 Windows Sockets 標準化"Big-endian"位元組順序模型，並提供此順序，和其他項目之間進行轉換的函式。 [CArchive](../mfc/reference/carchive-class.md)，不過可以搭配[CSocket](../mfc/reference/csocket-class.md)，會使用 （「 由小到大 」） 完全相反的順序，但`CArchive`負責為您的位元組順序轉換的詳細資料。 藉由使用此應用程式中的標準順序或使用 Windows Sockets 位元組順序的轉換函式，您可以讓您的程式碼更容易移植。  
  
 您要撰寫這兩個端點的通訊時，理想的情況下，使用 MFC 通訊端： 在兩端使用 MFC。 如果您要撰寫的應用程式將與其通訊非 MFC 應用程式，例如 FTP 伺服器，您可能需要管理位元組-交換自己先將資料傳遞至封存物件，使用 Windows Sockets 轉換常式**ntohs**， **ntohl**， **htons**，和**htonl**。 非 MFC 應用程式與通訊中使用這些函式的範例則顯示在本文稍後。  
  
> [!NOTE]
>  當另一端的通訊不 MFC 應用程式時，您也必須避免資料流 c + + 物件衍生自`CObject`成您封存因為接收者無法處理它們。 請參閱中的附註[Windows Sockets： 使用通訊端與封存](../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
 如需有關位元組順序的詳細資訊，請參閱 Windows Sockets 規格，可在 Windows SDK。  
  
## <a name="a-byte-order-conversion-example"></a>位元組順序轉換範例  
 下列範例示範序列化函式`CSocket`使用封存的物件。 它也說明在 Windows Sockets API 中使用的位元組順序的轉換函式。  
  
 本範例展示的狀況會在撰寫與您有原始程式碼無法存取非 MFC 伺服器應用程式通訊的用戶端。 在此案例中，您必須假設非 MFC 伺服器會使用標準網路位元組順序。 相反地，MFC 用戶端應用程式會使用`CArchive`物件`CSocket`物件，和`CArchive`使用"little Endian"的位元組順序，標準網路相反。  
  
 假設您計劃與其進行通訊的非 MFC 伺服器建立通訊協定訊息封包，如下所示：  
  
 [!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]  
  
 在 MFC 的用語，這就表示，如下所示：  
  
 [!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]  
  
 C + +`struct`是類別基本上相同的動作。 `Message`結構可以具有成員函式，例如`Serialize`上面所宣告成員函式。 `Serialize`成員函式可能會看起來像這樣：  
  
 [!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]  
  
 這個範例會呼叫的位元組順序轉換的資料，因為之間的一個 end 上非 MFC 伺服器應用程式的位元組順序清除不相符而`CArchive`另一端的 MFC 用戶端應用程式中使用。 此範例會說明數個 Windows Sockets 提供的位元組順序轉換函式。 下表描述這些函式。  
  
### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows Sockets 位元組順序的轉換函式  
  
|功能|用途|  
|--------------|-------------|  
|**ntohs**|從網路位元組順序轉換 16 位元數量，為主機位元組順序 （由小到大至 little Endian）。|  
|**ntohl**|從網路位元組順序轉換 32 位元數量，為主機位元組順序 （由小到大至 little Endian）。|  
|**Htons**|從主機位元組順序轉換的 16 位元數量，以網路位元組順序 （由小到大至 big Endian）。|  
|**Htonl**|從主機位元組順序轉換 32 位元數量，為網路位元組順序 （由小到大至 big Endian）。|  
  
 此範例中的另一個重點是在非 MFC 應用程式另一端的通訊端應用程式時，您必須避免執行類似下列：  
  
 `ar << pMsg;`  
  
 其中`pMsg`是衍生自類別的 c + + 物件的指標`CObject`。 這會傳送物件和伺服器相關聯的額外 MFC 資訊不了解，就好像 MFC 應用程式一樣。  
  
 如需詳細資訊，請參閱:  
  
-   [Windows Sockets：使用類別 CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets：背景](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets：資料流通訊端](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets：資料通訊端](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)

