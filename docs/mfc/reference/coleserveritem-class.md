---
title: "COleServerItem Class | Microsoft Docs"
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
  - "COleServerItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleServerItem class"
  - "OLE 伺服器應用程式, managing server documents"
  - "OLE 伺服器應用程式, server interfaces"
  - "OLE server documents"
  - "伺服器, OLE"
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleServerItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供介面給伺服器的 OLE 項目。  
  
## 語法  
  
```  
class COleServerItem : public CDocItem  
```  
  
## 成員  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleServerItem::COleServerItem](../Topic/COleServerItem::COleServerItem.md)|建構 `COleServerItem` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleServerItem::AddOtherClipboardData](../Topic/COleServerItem::AddOtherClipboardData.md)|在 `COleDataSource` 的展示和呈現格式物件。|  
|[COleServerItem::CopyToClipboard](../Topic/COleServerItem::CopyToClipboard.md)|將的項目複製到剪貼簿。|  
|[COleServerItem::DoDragDrop](../Topic/COleServerItem::DoDragDrop.md)|執行拖放作業。|  
|[COleServerItem::GetClipboardData](../Topic/COleServerItem::GetClipboardData.md)|取得資料來源以資料傳輸 \(拖放或剪貼簿\)。|  
|[COleServerItem::GetDocument](../Topic/COleServerItem::GetDocument.md)|傳回包含項目的伺服器文件。|  
|[COleServerItem::GetEmbedSourceData](../Topic/COleServerItem::GetEmbedSourceData.md)|取得 **CF\_EMBEDSOURCE** 資料為 OLE 項目。|  
|[COleServerItem::GetItemName](../Topic/COleServerItem::GetItemName.md)|傳回項目的名稱。  使用僅為連結的項目。|  
|[COleServerItem::GetLinkSourceData](../Topic/COleServerItem::GetLinkSourceData.md)|取得 `CF_LINKSOURCE` 資料為 OLE 項目。|  
|[COleServerItem::GetObjectDescriptorData](../Topic/COleServerItem::GetObjectDescriptorData.md)|取得 **CF\_OBJECTDESCRIPTOR** 資料為 OLE 項目。|  
|[COleServerItem::IsConnected](../Topic/COleServerItem::IsConnected.md)|表示此項目是否附加至 Active 容器。|  
|[COleServerItem::IsLinkedItem](../Topic/COleServerItem::IsLinkedItem.md)|指出項目是否表示連接的 OLE 項目。|  
|[COleServerItem::NotifyChanged](../Topic/COleServerItem::NotifyChanged.md)|更新會自動連結至更新的任何容器。|  
|[COleServerItem::OnDoVerb](../Topic/COleServerItem::OnDoVerb.md)|呼叫以執行動作。|  
|[COleServerItem::OnDraw](../Topic/COleServerItem::OnDraw.md)|呼叫時，容器需要繪製項目，需要的實作。|  
|[COleServerItem::OnDrawEx](../Topic/COleServerItem::OnDrawEx.md)|呼叫提供特定項目的繪圖。|  
|[COleServerItem::OnGetClipboardData](../Topic/COleServerItem::OnGetClipboardData.md)|呼叫以取得框架將會複製到剪貼簿中的資料。|  
|[COleServerItem::OnGetExtent](../Topic/COleServerItem::OnGetExtent.md)|呼叫由架構擷取 OLE 項目的大小。|  
|[COleServerItem::OnInitFromData](../Topic/COleServerItem::OnInitFromData.md)|呼叫框架初始化的 OLE 項目使用指定的資料傳輸物件的內容。|  
|[COleServerItem::OnQueryUpdateItems](../Topic/COleServerItem::OnQueryUpdateItems.md)|呼叫來判斷任何連結的項目是否需要更新。|  
|[COleServerItem::OnRenderData](../Topic/COleServerItem::OnRenderData.md)|為延遲轉譯的一部分，以擷取資料。|  
|[COleServerItem::OnRenderFileData](../Topic/COleServerItem::OnRenderFileData.md)|為延遲轉譯的一部分，擷取資料至 `CFile` 物件。|  
|[COleServerItem::OnRenderGlobalData](../Topic/COleServerItem::OnRenderGlobalData.md)|為延遲轉譯的一部分，擷取資料至 `HGLOBAL` 。|  
|[COleServerItem::OnSetColorScheme](../Topic/COleServerItem::OnSetColorScheme.md)|呼叫會將項目的色彩配置。|  
|[COleServerItem::OnSetData](../Topic/COleServerItem::OnSetData.md)|呼叫會將項目的資料。|  
|[COleServerItem::OnSetExtent](../Topic/COleServerItem::OnSetExtent.md)|呼叫框架設定 OLE 項目的大小。|  
|[COleServerItem::OnUpdate](../Topic/COleServerItem::OnUpdate.md)|呼叫，在文件的某個部分項目屬於時變更。|  
|[COleServerItem::OnUpdateItems](../Topic/COleServerItem::OnUpdateItems.md)|呼叫更新簡介快取在伺服器上文件中的所有項目。|  
|[COleServerItem::SetItemName](../Topic/COleServerItem::SetItemName.md)|設定項目的名稱。  使用僅為連結的項目。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[COleServerItem::GetDataSource](../Topic/COleServerItem::GetDataSource.md)|取得物件使用物件儲存格式轉換。|  
|[COleServerItem::OnHide](../Topic/COleServerItem::OnHide.md)|呼叫框架隱藏 OLE 項目。|  
|[COleServerItem::OnOpen](../Topic/COleServerItem::OnOpen.md)|呼叫由架構會顯示在其最上層視窗的 OLE 項目。|  
|[COleServerItem::OnShow](../Topic/COleServerItem::OnShow.md)|呼叫時，容器需要顯示項目。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[COleServerItem::m\_sizeExtent](../Topic/COleServerItem::m_sizeExtent.md)|告知數量的伺服器 OLE 項目為可見的。|  
  
## 備註  
 連結的項目可以代表部分或所有伺服器文件。  內嵌項目永遠表示整個伺服器文件。  
  
 `COleServerItem` 類別通常會定義由 OLE 系統動態連結程式庫 \(DLL\) \(DLLs\) 呼叫之可覆寫的成員函式，以回應從容器應用程式的需求。  這些成員函式允許容器應用程式間接操作項目以各種方式，例如透過顯示它，執行其動詞命令或擷取其資料的各種格式。  
  
 若要使用 `COleServerItem`，請從衍生類別並實作 [OnDraw](../Topic/COleServerItem::OnDraw.md) 和 [序列化](../Topic/CObject::Serialize.md) 成員函式。  當容器應用程式開啟複合文件時， `OnDraw` 函式提供項目的中繼檔表示，允許其顯示。  `CObject` 的 `Serialize` 函式提供項目之原生表示，允許內嵌項目將伺服器和容器應用程式之間。  [OnGetExtent](../Topic/COleServerItem::OnGetExtent.md) 提供項目的自然大小加入至容器，讓容器調整項目大小。  
  
 如需伺服器和相關主題的詳細資訊，請參閱本文 [伺服器:實作伺服器](../../mfc/servers-implementing-a-server.md) 和「建立容器 \(Container\)\/伺服器應用程式」本文 [容器:進階功能](../../mfc/containers-advanced-features.md)上。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleServerItem`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [MFC 範例 HIERSVR](../../top/visual-cpp-samples.md)   
 [CDocItem Class](../../mfc/reference/cdocitem-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleClientItem Class](../../mfc/reference/coleclientitem-class.md)   
 [COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)   
 [COleTemplateServer Class](../../mfc/reference/coletemplateserver-class.md)