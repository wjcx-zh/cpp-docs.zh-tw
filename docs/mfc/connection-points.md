---
title: "連接點 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IConnectionPoint
dev_langs: C++
helpviewer_keywords:
- IConnectionPoint interface
- connections, connection points
- OLE COM connection points
- MFC COM, connection points
- COM, connection points
- interfaces, IConnectionPoint
- MFC, COM support
- connection points [MFC]
- CCmdTarget class [MFC], and connection points
- sinks, connection points
ms.assetid: bc9fd7c7-8df6-4752-ac8c-0b177442c88d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0d8bbb131aa5d4ce1b12cba84c3928b80a8b2a7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="connection-points"></a>連接點
這篇文章說明如何實作連接點 （先前稱為 OLE 連接點 」） 使用 MFC 類別`CCmdTarget`和`CConnectionPoint`。  
  
 在過去，元件物件模型 (COM) 定義的一般機制 (**iunknown:: Queryinterface**)，允許物件來實作和公開介面中的功能。 不過，允許物件來公開其功能呼叫特定介面對應機制未定義。 也就是說，COM 會定義如何傳入的指標物件 （該物件的介面指標） 的處理，但它沒有明確的模型的輸出介面 （該物件保存其他物件的介面指標）。 COM 現在有一個模型，稱為連線點，支援此功能。  
  
 連線有兩個部分： 呼叫的來源，以及實作介面的物件呼叫的介面的物件呼叫接收。 連接點是由來源所公開的介面。 藉由公開連接點，為來源可讓接收來建立連接至其本身 （來源）。 透過連接點機制 ( **IConnectionPoint**介面)，接收介面的指標傳遞到來源物件。 此指標會提供來源接收實作一組成員函式的存取。 例如，若要引發事件接收實作，來源可以呼叫接收實作的適當方法。 下圖示範連接點剛剛所述。  
  
 ![實作連接點](../mfc/media/vc37lh1.gif "vc37lh1")  
實作的連接點  
  
 MFC 實作這種模式[CConnectionPoint](../mfc/reference/cconnectionpoint-class.md)和[CCmdTarget](../mfc/reference/ccmdtarget-class.md)類別。 類別衍生自**CConnectionPoint**實作**IConnectionPoint**介面，用來公開至其他物件的連接點。 類別衍生自`CCmdTarget`實作**IConnectionPointContainer**介面，可以列舉的所有物件的可用的連接點或尋找特定的連接點。  
  
 針對每個您類別中實作連接點，您必須宣告實作連接點的連線組件。 如果您實作一或多個連接點，您還必須在類別中宣告單一連接對應。 連接對應是 ActiveX 控制項所支援的連接點的資料表。  
  
 下列範例會示範簡單的連接對應，以及一個連接點。 第一個範例會宣告連接對應和點。第二個範例會實作對應和點。 請注意，`CMyClass`必須`CCmdTarget`-衍生的類別。 在第一個範例中，程式碼會插入在類別宣告中，在**保護**> 一節：  
  
 [!code-cpp[NVC_MFCConnectionPoints#1](../mfc/codesnippet/cpp/connection-points_1.h)]  
  
 `BEGIN_CONNECTION_PART`和**END_CONNECTION_PART**巨集宣告內嵌的類別， `XSampleConnPt` (衍生自`CConnectionPoint`)，實作這個特定的連接點。 如果您想要覆寫任何`CConnectionPoint`成員函式或加入您自己的成員函式，將它們宣告這些兩個巨集之間。 例如，`CONNECTION_IID`巨集覆寫`CConnectionPoint::GetIID`成員函式時這些兩個巨集之間。  
  
 在第二個範例中，程式碼會插入在控制項實作檔 （.cpp 檔）。 此程式碼會實作連接對應，其中包括連接點， `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../mfc/codesnippet/cpp/connection-points_2.cpp)]  
  
 如果您的類別有一個以上的連接點，插入其他`CONNECTION_PART`巨集之間`BEGIN_CONNECTION_MAP`和`END_CONNECTION_MAP`巨集。  
  
 最後，將呼叫加入`EnableConnections`類別的建構函式中。 例如:   
  
 [!code-cpp[NVC_MFCConnectionPoints#3](../mfc/codesnippet/cpp/connection-points_3.cpp)]  
  
 在插入這個程式碼之後, 您`CCmdTarget`-衍生的類別會公開的連接點**ISampleSink**介面。 下圖說明此範例。  
  
 ![使用 MFC 實作連接點](../mfc/media/vc37lh2.gif "vc37lh2")  
使用 MFC 實作連接點  
  
 連接點，通常支援 「 多點傳送 」 — 能力廣播至多個接收連線到相同的介面。 下列範例片段將示範如何逐一查看每個接收連接點上的多點傳送：  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../mfc/codesnippet/cpp/connection-points_4.cpp)]  
  
 這個範例會擷取目前的資料集的連接上`SampleConnPt`呼叫的連接點`CConnectionPoint::GetConnections`。 它接著會逐一連接並呼叫**ISampleSink::SinkFunc**上作用中的每個連接。  
  
## <a name="see-also"></a>請參閱  
 [MFC COM](../mfc/mfc-com.md)

