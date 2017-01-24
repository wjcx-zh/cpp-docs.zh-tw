---
title: "COleDataSource Class | Microsoft Docs"
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
  - "COleDataSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "剪貼簿 [C++], MFC 支援"
  - "剪貼簿 [C++], OLE 支援"
  - "COleDataSource class"
  - "data transfer [C++], OLE"
  - "drag and drop [C++], MFC 支援"
  - "IDataObject, MFC encapsulation"
  - "OLE [C++], uniform data transfer"
  - "OLE Clipboard [C++], 支援"
  - "OLE data transfer [C++]"
  - "uniform data transfer"
  - "uniform data transfer, OLE"
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDataSource Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

做為應用程式放置資料將提供，例如剪貼簿或拖放作業的快取資料轉換作業期間，。  
  
## 語法  
  
```  
class COleDataSource : public CCmdTarget  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleDataSource::COleDataSource](../Topic/COleDataSource::COleDataSource.md)|建構 `COleDataSource` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleDataSource::CacheData](../Topic/COleDataSource::CacheData.md)|以指定的格式來提供資料使用 **STGMEDIUM** 結構。|  
|[COleDataSource::CacheGlobalData](../Topic/COleDataSource::CacheGlobalData.md)|使用 `HGLOBAL`，提供在指定格式的資料。|  
|[COleDataSource::DelayRenderData](../Topic/COleDataSource::DelayRenderData.md)|使用延遲轉譯，提供在指定格式的資料。|  
|[COleDataSource::DelayRenderFileData](../Topic/COleDataSource::DelayRenderFileData.md)|提供以指定格式的資料。 `CFile` 指標。|  
|[COleDataSource::DelaySetData](../Topic/COleDataSource::DelaySetData.md)|呼叫以在 `OnSetData`支援的所有格式。|  
|[COleDataSource::DoDragDrop](../Topic/COleDataSource::DoDragDrop.md)|對資料來源的拖放作業。|  
|[COleDataSource::Empty](../Topic/COleDataSource::Empty.md)|空白資料 `COleDataSource` 物件。|  
|[COleDataSource::FlushClipboard](../Topic/COleDataSource::FlushClipboard.md)|呈現所有資料加入至剪貼簿。|  
|[COleDataSource::GetClipboardOwner](../Topic/COleDataSource::GetClipboardOwner.md)|驗證在剪貼簿上的資料仍然存在。|  
|[COleDataSource::OnRenderData](../Topic/COleDataSource::OnRenderData.md)|為延遲轉譯的一部分，以擷取資料。|  
|[COleDataSource::OnRenderFileData](../Topic/COleDataSource::OnRenderFileData.md)|為延遲轉譯的一部分，擷取資料至 `CFile` 。|  
|[COleDataSource::OnRenderGlobalData](../Topic/COleDataSource::OnRenderGlobalData.md)|為延遲轉譯的一部分，擷取資料至 `HGLOBAL` 。|  
|[COleDataSource::OnSetData](../Topic/COleDataSource::OnSetData.md)|呼叫取代 `COleDataSource` 的資料物件。|  
|[COleDataSource::SetClipboard](../Topic/COleDataSource::SetClipboard.md)|在剪貼簿上放置 `COleDataSource` 物件。|  
  
## 備註  
 您可以直接建立 OLE 資料來源。  或者， [COleClientItem](../../mfc/reference/coleclientitem-class.md) 和 [COleServerItem](../../mfc/reference/coleserveritem-class.md) 類別建立 OLE 資料來源以回應其 `CopyToClipboard` 和 `DoDragDrop` 成員函式。  提供概要說明請參閱 [COleServerItem::CopyToClipboard](../Topic/COleServerItem::CopyToClipboard.md) 。  覆寫您的用戶端項目或伺服器項目類別的 `OnGetClipboardData` 成員函式將額外的剪貼簿格式套用至指定 `CopyToClipboard` 或 `DoDragDrop` 成員函式所建立的 OLE 資料來源的資料。  
  
 每當您想要的資料傳輸，準備使用您的資料，最適合的方法應該建立這個類別的物件、將資料填入其中。  已插入資料來源的方式直接影響是否立即提供資料 \(直接轉換\) 或在需要時 \(延遲轉譯\)。  對於您傳入剪貼簿格式會使用的每個剪貼簿格式 \(以及選擇性 [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) 結構\) 提供資料，呼叫 [DelayRenderData](../Topic/COleDataSource::DelayRenderData.md)。  
  
 如需資料來源和資料傳輸的詳細資訊，請參閱本文 [資料物件和資料來源 \(Object Linking\)](../../mfc/data-objects-and-data-sources-ole.md)。  此外，文件 [剪貼簿主題](../../mfc/clipboard.md) 說明 OLE 剪貼簿機制。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDataSource`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [MFC 範例 HIERSVR](../../top/visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../top/visual-cpp-samples.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleDataObject Class](../../mfc/reference/coledataobject-class.md)