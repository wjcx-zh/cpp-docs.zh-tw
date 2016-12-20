---
title: "CConnectionPoint Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CConnectionPoint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CConnectionPoint class"
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
caps.latest.revision: 20
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CConnectionPoint Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定義用於之介面的特定型別與其他 OLE 物件進行通訊，稱為「連接點」。  
  
## 語法  
  
```  
class CConnectionPoint : public CCmdTarget  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CConnectionPoint::CConnectionPoint](../Topic/CConnectionPoint::CConnectionPoint.md)|建構 `CConnectionPoint` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CConnectionPoint::GetConnections](../Topic/CConnectionPoint::GetConnections.md)|擷取在連接對應的所有連接點。|  
|[CConnectionPoint::GetContainer](../Topic/CConnectionPoint::GetContainer.md)|擷取擁有連接對應控制項的容器。|  
|[CConnectionPoint::GetIID](../Topic/CConnectionPoint::GetIID.md)|擷取連接點的介面 ID。|  
|[CConnectionPoint::GetMaxConnections](../Topic/CConnectionPoint::GetMaxConnections.md)|擷取控制項支援的連接點的最大數目。|  
|[CConnectionPoint::GetNextConnection](../Topic/CConnectionPoint::GetNextConnection.md)|擷取指標連接項目在 `pos`。|  
|[CConnectionPoint::GetStartPosition](../Topic/CConnectionPoint::GetStartPosition.md)|將傳回可傳遞至 `GetNextConnection` 呼叫的 **位置** 值開始對應反覆項目。|  
|[CConnectionPoint::OnAdvise](../Topic/CConnectionPoint::OnAdvise.md)|呼叫框架，其在建立或中斷連接時。|  
|[CConnectionPoint::QuerySinkInterface](../Topic/CConnectionPoint::QuerySinkInterface.md)|擷取指標所要求的介面指標。|  
  
## 備註  
 不同於一般 OLE 介面，用來實作和公開 OLE 控制項，連接點實作功能的輸出介面可以啟始對其他物件的動作，例如引發事件和變更告知。  
  
 連接都包含兩個部分:呼叫介面的物件，稱為「來源」，並且實作介面的物件，稱為「接收」。透過公開連接點，來源允許接收建立與其本身的連接。  在連接點機制，來源物件會取得指標存取一組接收實作的成員函式。  例如，引發接收實作的事件來源，可以呼叫接收的實作中適當的方法。  
  
 根據預設， `COleControl`衍生類別會實作兩個連接點:一個事件的另一個屬性變更告知的。  這些連接，並使用類別，為事件引發和用來通知接收 \(例如，控制項的容器\)，當屬性值變更時。  支援 OLE 控制項也提供的實作其他連接點。  針對控制項類別實作的每個不同的連接點，則必須宣告為「連接部分」實作連接點。  如果您實作一或多個連接點，也需要宣告單一「連接對應」在您的控制項類別。  
  
 下列範例示範簡單的連接對應和連接點 `Sample` OLE 控制項的功能，包括程式碼的兩個區段:第一個部分宣告連接對應和上;第二個實作此導覽並指向。  第一個片段插入控制項類別的宣告，如 `protected` 區段中:  
  
 [!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/CPP/cconnectionpoint-class_1.h)]  
  
 `BEGIN_CONNECTION_PART` 和 `END_CONNECTION_PART` 巨集會宣告內嵌類別， `XSampleConnPt` \(衍生自\) `CConnectionPoint`實作這個特定連接點。  如果您要覆寫任何 `CConnectionPoint` 成員函式或加入自己的成員函式中，宣告它們在這兩個巨集之間。  例如， `CONNECTION_IID` 巨集覆寫 `CConnectionPoint::GetIID` 成員函式，當位於這兩個巨集之間。  
  
 第二個程式碼片段插入實作檔 \(.CPP\) 的控制項類別。  這個程式碼會實作連接對應，包括其他連接點， `SampleConnPt`:  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/CPP/cconnectionpoint-class_2.cpp)]  
  
 一旦插入了這些程式碼片段中，範例 OLE 控制項公開 **ISampleSink** 介面的連接點。  
  
 通常，連接點支援「多點傳送」，而能夠廣播至多接收連接到相同的介面。  下列程式碼片段示範如何逐一查看完成多點傳送透過連接點的每個接收:  
  
 [!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/CPP/cconnectionpoint-class_3.cpp)]  
  
 這個範例會擷取目前在 `SampleConnPt` 連接點的連接以呼叫 `CConnectionPoint::GetConnections`。  它會將連接然後逐一查看並呼叫每個有效連結的 `ISampleSink::SinkFunc` 。  
  
 如需使用 `CConnectionPoint`的詳細資訊，請參閱本文 [連接點](../../mfc/connection-points.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CConnectionPoint`  
  
## 需求  
 **Header:** afxdisp.h  
  
## 請參閱  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)