---
title: "連接點 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IConnectionPoint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCmdTarget 類別, 和連接點"
  - "COM, 連接點"
  - "連接點 [C++]"
  - "連接, 連接點"
  - "IConnectionPoint 介面"
  - "介面, IConnectionPoint"
  - "MFC [C++], COM 支援"
  - "MFC COM, 連接點"
  - "OLE COM 連接點"
  - "接收器, 連接點"
ms.assetid: bc9fd7c7-8df6-4752-ac8c-0b177442c88d
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 連接點
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何實作連接點 \(先前稱為 OLE 連接點\) 使用 MFC 類別 `CCmdTarget` ，以及 `CConnectionPoint`。  
  
 在過去，元件物件模型 \(COM\) \(COM\) 定義允許物件實作和公開介面的功能的一般機制 \(**IUnknown::QueryInterface**\)。  不過，可以讓物件公開其功能呼叫特定介面的對應機制未定義。  即 COM 定義的物件 \(該物件的介面指標的傳入的指標\) 的處理方式的，不過，它不會輸出介面 \(物件來保留對其他物件的介面\) 的指標明確的模型。  COM 現在有一個模型，呼叫連接點，支援這項功能。  
  
 連接有兩個部分:呼叫介面的物件，稱為來源和實作介面的物件，接收呼叫。  連接點是來源公開的介面。  透過公開連接點，來源允許接收建立本身 \(來源\)。  在連接點機制 \( **IConnectionPoint** \) 介面，會接收介面指標傳遞給來源物件。  這個指標提供來源以一組的接收實作的存取成員函式。  例如，引發接收實作的事件來源，可以呼叫所接收的實作適當的方法。  下圖顯示上述的連接點。  
  
 ![實作的連接點](../mfc/media/vc37lh1.png "vc37LH1")  
已實作的連接點。  
  
 MFC 實作在 [CConnectionPoint](../mfc/reference/cconnectionpoint-class.md) 和 [CCmdTarget](../mfc/reference/ccmdtarget-class.md) 類別的模型。  從 **CConnectionPoint** 衍生的類別實作 **IConnectionPoint** 介面，用來公開給其他物件的連接點。  衍生自 `CCmdTarget` 的類別實作 **IConnectionPointContainer** 介面，可以列舉所有物件的可用連接點或尋找特定連接點。  
  
 為您的類別實作的每個連接點，則必須宣告實作連接點的連接部分。  如果您實作一或多個連接點，也必須宣告在類別的單一連接對應。  連接對應是 ActiveX 控制項支援的聯合資料表。  
  
 下列範例示範簡單的連接對應和連接點。  第一個範例宣告連接對應和點;第二個範例 Implementation Map 和點。  請注意 `CMyClass`必須是 `CCmdTarget`衍生類別。  在第一個範例中，程式碼在類別宣告中插入，在 **protected** 區段底下:  
  
 [!code-cpp[NVC_MFCConnectionPoints#1](../mfc/codesnippet/CPP/connection-points_1.h)]  
  
 `BEGIN_CONNECTION_PART` 和 **END\_CONNECTION\_PART** 巨集來宣告內嵌類別， `XSampleConnPt` \(衍生自 `CConnectionPoint`\)，實作這個特定連接點。  如果您要覆寫任何 `CConnectionPoint` 成員函式或加入成員函式宣告，它們在這兩個巨集之間。  例如， `CONNECTION_IID` 巨集覆寫 `CConnectionPoint::GetIID` 成員函式時，將在這兩個巨集之間。  
  
 在第二個範例中，程式碼會在控制項的實作檔 \(.cpp 檔\) 插入。  這個程式碼會實作連接點對應，包括連接點， `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../mfc/codesnippet/CPP/connection-points_2.cpp)]  
  
 如果您的類別有多個連接點時，在 `BEGIN_CONNECTION_MAP` 和 `END_CONNECTION_MAP` 巨集之間的其他 `CONNECTION_PART` 巨集。  
  
 最後，請將呼叫加入至類別的建構函式的 `EnableConnections` 。  例如：  
  
 [!code-cpp[NVC_MFCConnectionPoints#3](../mfc/codesnippet/CPP/connection-points_3.cpp)]  
  
 一旦插入此程式碼，您的 `CCmdTarget`衍生類別公開 **ISampleSink** 介面的連接點。  下圖顯示範例。  
  
 ![使用 MFC 實作的連接點](../mfc/media/vc37lh2.png "vc37LH2")  
連接點實作與 MFC  
  
 通常，連接點支援多點傳送」—能力廣播至多接收連接到相同的介面。  下列程式碼片段示範如何逐一查看多點傳送傳入連接點的各個接收:  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../mfc/codesnippet/CPP/connection-points_4.cpp)]  
  
 這個範例會擷取目前設定 `SampleConnPt` 連接點的連接與呼叫 `CConnectionPoint::GetConnections`。  它會透過連接然後逐一查看並在每一個有效連接的 **ISampleSink::SinkFunc** 。  
  
## 請參閱  
 [MFC COM](../mfc/mfc-com.md)