---
title: "COleClientItem Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleClientItem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "client items and OLE containers"
  - "COleClientItem class"
  - "container interface class"
  - "OLE client item class"
  - "OLE containers, client items"
  - "OLE containers, interface class"
ms.assetid: 7f571b7c-2758-4839-847a-0cf1ef643128
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# COleClientItem Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

定義容器介面為 OLE 項目。  
  
## 語法  
  
```  
class COleClientItem : public CDocItem  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleClientItem::COleClientItem](../Topic/COleClientItem::COleClientItem.md)|建構 `COleClientItem` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleClientItem::Activate](../Topic/COleClientItem::Activate.md)|開啟作業的 OLE 項目然後執行指定的動作。|  
|[COleClientItem::ActivateAs](../Topic/COleClientItem::ActivateAs.md)|啟動項目做為另一個型別。|  
|[COleClientItem::AttachDataObject](../Topic/COleClientItem::AttachDataObject.md)|存取在 OLE 物件的資料。|  
|[COleClientItem::CanCreateFromData](../Topic/COleClientItem::CanCreateFromData.md)|表示容器應用程式是否可建立一個內嵌物件。|  
|[COleClientItem::CanCreateLinkFromData](../Topic/COleClientItem::CanCreateLinkFromData.md)|表示容器應用程式是否可建立一個連結物件。|  
|[COleClientItem::CanPaste](../Topic/COleClientItem::CanPaste.md)|指出剪貼簿是否包含可內嵌或靜態 OLE 項目。|  
|[COleClientItem::CanPasteLink](../Topic/COleClientItem::CanPasteLink.md)|指出剪貼簿是否包含可連接的 OLE 項目。|  
|[COleClientItem::Close](../Topic/COleClientItem::Close.md)|關閉已連結至伺服器，但不會終結 OLE 項目。|  
|[COleClientItem::ConvertTo](../Topic/COleClientItem::ConvertTo.md)|轉換項目至另一個型別。|  
|[COleClientItem::CopyToClipboard](../Topic/COleClientItem::CopyToClipboard.md)|複製 OLE 項目複製到剪貼簿。|  
|[COleClientItem::CreateCloneFrom](../Topic/COleClientItem::CreateCloneFrom.md)|建立現有項目的複本。|  
|[COleClientItem::CreateFromClipboard](../Topic/COleClientItem::CreateFromClipboard.md)|若要從剪貼簿的內嵌項目。|  
|[COleClientItem::CreateFromData](../Topic/COleClientItem::CreateFromData.md)|若要從資料物件的內嵌項目。|  
|[COleClientItem::CreateFromFile](../Topic/COleClientItem::CreateFromFile.md)|建立內嵌項目從檔案。|  
|[COleClientItem::CreateLinkFromClipboard](../Topic/COleClientItem::CreateLinkFromClipboard.md)|若要從剪貼簿上連結的項目。|  
|[COleClientItem::CreateLinkFromData](../Topic/COleClientItem::CreateLinkFromData.md)|若要從資料物件中的連結的項目。|  
|[COleClientItem::CreateLinkFromFile](../Topic/COleClientItem::CreateLinkFromFile.md)|建立連結的項目從檔案。|  
|[COleClientItem::CreateNewItem](../Topic/COleClientItem::CreateNewItem.md)|透過啟動伺服器應用程式建立新的內嵌項目。|  
|[COleClientItem::CreateStaticFromClipboard](../Topic/COleClientItem::CreateStaticFromClipboard.md)|若要從剪貼簿的靜態項目。|  
|[COleClientItem::CreateStaticFromData](../Topic/COleClientItem::CreateStaticFromData.md)|若要從資料物件的靜態項目。|  
|[COleClientItem::Deactivate](../Topic/COleClientItem::Deactivate.md)|停用項目。|  
|[COleClientItem::DeactivateUI](../Topic/COleClientItem::DeactivateUI.md)|還原容器應用程式的使用者介面 \(UI\) 還原為其原始狀態。|  
|[COleClientItem::Delete](../Topic/COleClientItem::Delete.md)|如果它是連結的項目，刪除或關閉 OLE 項目。|  
|[COleClientItem::DoDragDrop](../Topic/COleClientItem::DoDragDrop.md)|執行拖放作業。|  
|[COleClientItem::DoVerb](../Topic/COleClientItem::DoVerb.md)|執行指定的動作。|  
|[COleClientItem::Draw](../Topic/COleClientItem::Draw.md)|繪製 OLE 項目。|  
|[COleClientItem::GetActiveView](../Topic/COleClientItem::GetActiveView.md)|取得項目就地啟動的檢視。|  
|[COleClientItem::GetCachedExtent](../Topic/COleClientItem::GetCachedExtent.md)|傳回 OLE 項目的矩形界限。|  
|[COleClientItem::GetClassID](../Topic/COleClientItem::GetClassID.md)|取得目前項目的類別 ID。.|  
|[COleClientItem::GetClipboardData](../Topic/COleClientItem::GetClipboardData.md)|取得在剪貼簿上呼叫 `CopyToClipboard` 成員函式的資料。|  
|[COleClientItem::GetDocument](../Topic/COleClientItem::GetDocument.md)|傳回包含目前項目的 `COleDocument` 物件。|  
|[COleClientItem::GetDrawAspect](../Topic/COleClientItem::GetDrawAspect.md)|取得呈現之項目的目前檢視。|  
|[COleClientItem::GetExtent](../Topic/COleClientItem::GetExtent.md)|傳回 OLE 項目的矩形界限。|  
|[COleClientItem::GetIconFromRegistry](../Topic/COleClientItem::GetIconFromRegistry.md)|Retrives 為圖示的控制代碼與特定 CLSID 的伺服器。|  
|[COleClientItem::GetIconicMetafile](../Topic/COleClientItem::GetIconicMetafile.md)|取得此中繼檔用於繪製項目的圖示。|  
|[COleClientItem::GetInPlaceWindow](../Topic/COleClientItem::GetInPlaceWindow.md)|會將指標傳至項目的就地編輯視窗。|  
|[COleClientItem::GetItemState](../Topic/COleClientItem::GetItemState.md)|取得項目的目前狀態。|  
|[COleClientItem::GetLastStatus](../Topic/COleClientItem::GetLastStatus.md)|要傳回最後一個 OLE 作業的狀態。|  
|[COleClientItem::GetLinkUpdateOptions](../Topic/COleClientItem::GetLinkUpdateOptions.md)|傳回一個連結的項目 \(進階功能\) 更新模式。|  
|[COleClientItem::GetType](../Topic/COleClientItem::GetType.md)|傳回型別 \(內嵌，連接或靜態\) 的 OLE 項目。|  
|[COleClientItem::GetUserType](../Topic/COleClientItem::GetUserType.md)|取得描述項目型別的字串。|  
|[COleClientItem::IsInPlaceActive](../Topic/COleClientItem::IsInPlaceActive.md)|不過，如果項目是就地啟動，則會傳回 `TRUE` 。|  
|[COleClientItem::IsLinkUpToDate](../Topic/COleClientItem::IsLinkUpToDate.md)|如果連結的項目都是最新的原始程式檔，它會傳回 **是** 。|  
|[COleClientItem::IsModified](../Topic/COleClientItem::IsModified.md)|傳回 `TRUE` 後，如果修改項目，自上次儲存。|  
|[COleClientItem::IsOpen](../Topic/COleClientItem::IsOpen.md)|不過，如果項目已經在伺服器應用程式，則會傳回 `TRUE` 。|  
|[COleClientItem::IsRunning](../Topic/COleClientItem::IsRunning.md)|不過，如果項目的伺服器應用程式執行時，會傳回 `TRUE` 。|  
|[COleClientItem::OnActivate](../Topic/COleClientItem::OnActivate.md)|呼叫以告知架構項目則會啟動。|  
|[COleClientItem::OnActivateUI](../Topic/COleClientItem::OnActivateUI.md)|呼叫以告知架構項目則會啟動而且應該會顯示其使用者介面。|  
|[COleClientItem::OnChange](../Topic/COleClientItem::OnChange.md)|呼叫方法，則伺服器變更的 OLE 項目。  需要的實作。|  
|[COleClientItem::OnDeactivate](../Topic/COleClientItem::OnDeactivate.md)|呼叫由架構，在停用項目。|  
|[COleClientItem::OnDeactivateUI](../Topic/COleClientItem::OnDeactivateUI.md)|呼叫框架，該伺服器已移除其就地使用者介面。|  
|[COleClientItem::OnGetClipboardData](../Topic/COleClientItem::OnGetClipboardData.md)|呼叫框架取得資料複製到剪貼簿。|  
|[COleClientItem::OnInsertMenus](../Topic/COleClientItem::OnInsertMenus.md)|呼叫由架構建立複合功能表。|  
|[COleClientItem::OnRemoveMenus](../Topic/COleClientItem::OnRemoveMenus.md)|呼叫框架從複合功能表移除容器的功能表。|  
|[COleClientItem::OnSetMenu](../Topic/COleClientItem::OnSetMenu.md)|呼叫由架構安裝和移除複合功能表。|  
|[COleClientItem::OnShowControlBars](../Topic/COleClientItem::OnShowControlBars.md)|呼叫由架構來顯示和隱藏控制項的資料行。|  
|[COleClientItem::OnUpdateFrameTitle](../Topic/COleClientItem::OnUpdateFrameTitle.md)|呼叫框架更新框架視窗的標題列。|  
|[COleClientItem::ReactivateAndUndo](../Topic/COleClientItem::ReactivateAndUndo.md)|重新啟動項目並復原最後就地編輯作業。|  
|[COleClientItem::Release](../Topic/COleClientItem::Release.md)|若已開啟，釋放與 OLE 連結項目的連接並關閉。  不會終結用戶端項目。|  
|[COleClientItem::Reload](../Topic/COleClientItem::Reload.md)|在呼叫之後重新載入專案。 `ActivateAs`。|  
|[COleClientItem::Run](../Topic/COleClientItem::Run.md)|執行應用程式相關聯的項目。|  
|[COleClientItem::SetDrawAspect](../Topic/COleClientItem::SetDrawAspect.md)|設定要呈現的項目的目前檢視。|  
|[COleClientItem::SetExtent](../Topic/COleClientItem::SetExtent.md)|設定 OLE 項目的週框 \(Bounding Rectangle\)。|  
|[COleClientItem::SetHostNames](../Topic/COleClientItem::SetHostNames.md)|若要設定伺服器時，便會顯示編輯 OLE 項目的名稱。|  
|[COleClientItem::SetIconicMetafile](../Topic/COleClientItem::SetIconicMetafile.md)|快取提供繪製項目圖示使用的此中繼檔。|  
|[COleClientItem::SetItemRects](../Topic/COleClientItem::SetItemRects.md)|設定項目的週框。|  
|[COleClientItem::SetLinkUpdateOptions](../Topic/COleClientItem::SetLinkUpdateOptions.md)|設定連結的項目 \(進階功能\) 更新模式。|  
|[COleClientItem::SetPrintDevice](../Topic/COleClientItem::SetPrintDevice.md)|設定這個用戶端項目的列印目標裝置。|  
|[COleClientItem::UpdateLink](../Topic/COleClientItem::UpdateLink.md)|已更新項目的展示快取。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[COleClientItem::CanActivate](../Topic/COleClientItem::CanActivate.md)|呼叫由架構判斷就地啟動是否允許。|  
|[COleClientItem::OnChangeItemPosition](../Topic/COleClientItem::OnChangeItemPosition.md)|呼叫框架，該項目的位置而改變。|  
|[COleClientItem::OnDeactivateAndUndo](../Topic/COleClientItem::OnDeactivateAndUndo.md)|呼叫堆疊中啟動之後繼續執行。|  
|[COleClientItem::OnDiscardUndoState](../Topic/COleClientItem::OnDiscardUndoState.md)|呼叫框架捨棄項目的復原狀態資訊。|  
|[COleClientItem::OnGetClipRect](../Topic/COleClientItem::OnGetClipRect.md)|呼叫由架構來取得項目的裁剪矩形座標。|  
|[COleClientItem::OnGetItemPosition](../Topic/COleClientItem::OnGetItemPosition.md)|呼叫框架取得項目的位置 \(相對於檢視。|  
|[COleClientItem::OnGetWindowContext](../Topic/COleClientItem::OnGetWindowContext.md)|呼叫框架，當項目就地啟動。|  
|[COleClientItem::OnScrollBy](../Topic/COleClientItem::OnScrollBy.md)|呼叫框架將項目捲動到檢視。|  
|[COleClientItem::OnShowItem](../Topic/COleClientItem::OnShowItem.md)|呼叫框架 \(Frame\) 的 OLE 項目。|  
  
## 備註  
 一個 OLE 項目表示資料，建立和維護由伺服器應用程式，可以「完美地」會納入文件中，使它對使用者是單一文件。  結果會是「複合文件」修剪 OLE 項目和所包含的檔案。  
  
 可以嵌入這個 OLE 項目或連結。  如果它內嵌，做為複合文件的一部分，它的資料儲存。  如果連接，但它的資料會儲存為伺服器應用程式建立個別的檔案中，，且該檔案中只有一個連結在複合檔案內。  所有的 OLE 項目包含指定應該呼叫編輯它們的伺服器應用程式的資訊。  
  
 `COleClientItem` 定義呼叫以回應伺服器應用程式的要求數個可覆寫的函式;這些 overridables 通常做為告知。  這可讓伺服器應用程式通知使用者所做的變更，在編輯 OLE 項目的容器變更，或擷取在編譯期間所需的資訊。  
  
 `COleClientItem` 可以與 [COleDocument](../../mfc/reference/coledocument-class.md)、 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)或 [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) 類別。  若要使用 `COleClientItem`，請從衍生類別並實作 [OnChange](../Topic/COleClientItem::OnChange.md) 成員函式，定義容器如何回應對的變更和項目。  若要支援就地啟動，請覆寫 [OnGetItemPosition](../Topic/COleClientItem::OnGetItemPosition.md) 成員函式。  這個函式會提供有關 OLE 項目的顯示位置的資訊。  
  
 如需使用容器介面的詳細資訊，請參閱 Microsoft 知識庫文件 [容器:實作容器](../../mfc/containers-implementing-a-container.md) 和 [啟動](../../mfc/activation-cpp.md)。  
  
> [!NOTE]
>  [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] 參考內嵌資源和連結的項目以「物件」是指項目的型別為「類別」。此參考使用詞彙「項目」\(Item\) 與對應的 C\+\+ 物件差異 OLE 實體和詞彙「type」的 C\+\+ 類別差異 OLE 分類。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleClientItem`  
  
## 需求  
 **Header:** afxole.h  
  
## 請參閱  
 [MFC MFCBIND 範例](../../top/visual-cpp-samples.md)   
 [MFC 範例 OCLIENT](../../top/visual-cpp-samples.md)   
 [CDocItem Class](../../mfc/reference/cdocitem-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)