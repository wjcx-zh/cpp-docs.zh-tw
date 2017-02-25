---
title: "CRenderTarget 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRenderTarget"
  - "afxrendertarget/CRenderTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRenderTarget 類別"
ms.assetid: 30d1607d-68d3-4d14-ac36-fdbd0ef903a1
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CRenderTarget 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1RenderTarget 的包裝函式。  
  
## 語法  
  
```  
class CRenderTarget : public CObject;  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CRenderTarget::CRenderTarget](../Topic/CRenderTarget::CRenderTarget.md)|建構 CRenderTarget 物件。|  
|[CRenderTarget::~CRenderTarget](../Topic/CRenderTarget::~CRenderTarget.md)|解構函式。  當正在終結轉譯目標物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRenderTarget::Attach](../Topic/CRenderTarget::Attach.md)|將現有的轉譯目標介面附加至物件|  
|[CRenderTarget::BeginDraw](../Topic/CRenderTarget::BeginDraw.md)|初始化這個轉譯目標上的繪圖。|  
|[CRenderTarget::Clear](../Topic/CRenderTarget::Clear.md)|將繪圖區清除為指定的色彩。|  
|[CRenderTarget::COLORREF\_TO\_D2DCOLOR](../Topic/CRenderTarget::COLORREF_TO_D2DCOLOR.md)|將 GDI 色彩和 Alpha 值轉換為 D2D1\_COLOR\_F 物件。|  
|[CRenderTarget::CreateCompatibleRenderTarget](../Topic/CRenderTarget::CreateCompatibleRenderTarget.md)|建立新的點陣圖轉譯目標，以供在相容於目前轉譯目標的中繼幕後繪圖期間使用。|  
|[CRenderTarget::Destroy](../Topic/CRenderTarget::Destroy.md)|刪除一個或多個資源|  
|[CRenderTarget::Detach](../Topic/CRenderTarget::Detach.md)|將轉譯目標介面與其物件中斷連結|  
|[CRenderTarget::DrawBitmap](../Topic/CRenderTarget::DrawBitmap.md)|繪製指定之 IDWriteTextLayout 物件所描述的格式化文字。|  
|[CRenderTarget::DrawEllipse](../Topic/CRenderTarget::DrawEllipse.md)|使用指定的筆劃樣式繪製指定之橢圓形的外框。|  
|[CRenderTarget::DrawGeometry](../Topic/CRenderTarget::DrawGeometry.md)|使用指定的筆劃樣式繪製指定之幾何的外框。|  
|[CRenderTarget::DrawGlyphRun](../Topic/CRenderTarget::DrawGlyphRun.md)|繪製指定的字符。|  
|[CRenderTarget::DrawLine](../Topic/CRenderTarget::DrawLine.md)|使用指定的筆劃樣式，在指定的點之間繪製線條。|  
|[CRenderTarget::DrawRectangle](../Topic/CRenderTarget::DrawRectangle.md)|繪製具有指定之維度和筆劃樣式的矩形外框。|  
|[CRenderTarget::DrawRoundedRectangle](../Topic/CRenderTarget::DrawRoundedRectangle.md)|使用指定的筆劃樣式繪製指定之圓角矩形的外框。|  
|[CRenderTarget::DrawText](../Topic/CRenderTarget::DrawText.md)|使用 IDWriteTextFormat 物件提供的格式資訊，繪製指定的文字。|  
|[CRenderTarget::DrawTextLayout](../Topic/CRenderTarget::DrawTextLayout.md)|繪製指定之 IDWriteTextLayout 物件所描述的格式化文字。|  
|[CRenderTarget::EndDraw](../Topic/CRenderTarget::EndDraw.md)|結束轉譯目標上的繪製作業，並顯示目前的錯誤狀態和相關聯的標籤。|  
|[CRenderTarget::FillEllipse](../Topic/CRenderTarget::FillEllipse.md)|繪製指定之橢圓形的內部。|  
|[CRenderTarget::FillGeometry](../Topic/CRenderTarget::FillGeometry.md)|繪製指定之幾何的內部。|  
|[CRenderTarget::FillMesh](../Topic/CRenderTarget::FillMesh.md)|繪製指定之網狀的內部。|  
|[CRenderTarget::FillOpacityMask](../Topic/CRenderTarget::FillOpacityMask.md)|將指定之點陣圖所描述的不透明度遮罩套用至筆刷，並使用該筆刷來繪製轉譯目標的區域。|  
|[CRenderTarget::FillRectangle](../Topic/CRenderTarget::FillRectangle.md)|繪製指定之矩形的內部。|  
|[CRenderTarget::FillRoundedRectangle](../Topic/CRenderTarget::FillRoundedRectangle.md)|繪製指定之圓角矩形的內部。|  
|[CRenderTarget::Flush](../Topic/CRenderTarget::Flush.md)|執行所有暫止的繪圖命令。|  
|[CRenderTarget::GetAntialiasMode](../Topic/CRenderTarget::GetAntialiasMode.md)|擷取非文字繪製作業的目前消除鋸齒模式。|  
|[CRenderTarget::GetDpi](../Topic/CRenderTarget::GetDpi.md)|傳回轉譯目標的 Dots Per Inch \(DPI\)|  
|[CRenderTarget::GetMaximumBitmapSize](../Topic/CRenderTarget::GetMaximumBitmapSize.md)|取得轉譯目標所支援之任何一個點陣圖維度大小的最大值，以裝置獨立單位 \(像素\) 為單位|  
|[CRenderTarget::GetPixelFormat](../Topic/CRenderTarget::GetPixelFormat.md)|擷取轉譯目標的像素格式和 Alpha 模式|  
|[CRenderTarget::GetPixelSize](../Topic/CRenderTarget::GetPixelSize.md)|傳回轉譯目標的大小 \(以裝置像素為單位\)|  
|[CRenderTarget::GetRenderTarget](../Topic/CRenderTarget::GetRenderTarget.md)|傳回 ID2D1RenderTarget 介面|  
|[CRenderTarget::GetSize](../Topic/CRenderTarget::GetSize.md)|傳回轉譯目標的大小 \(以裝置獨立畫素為單位\)|  
|[CRenderTarget::GetTags](../Topic/CRenderTarget::GetTags.md)|取得後續繪製作業的標籤。|  
|[CRenderTarget::GetTextAntialiasMode](../Topic/CRenderTarget::GetTextAntialiasMode.md)|取得文字及字符繪製作業的目前消除鋸齒模式。|  
|[CRenderTarget::GetTextRenderingParams](../Topic/CRenderTarget::GetTextRenderingParams.md)|擷取轉譯目標的目前文字呈現選項。|  
|[CRenderTarget::GetTransform](../Topic/CRenderTarget::GetTransform.md)|將指定的轉換套用至轉譯目標，並取代現有的轉換。  所有後續的繪製作業都會在轉換的空間中發生。|  
|[CRenderTarget::IsSupported](../Topic/CRenderTarget::IsSupported.md)|表示轉譯目標是否支援指定的屬性|  
|[CRenderTarget::IsValid](../Topic/CRenderTarget::IsValid.md)|檢查資源有效性|  
|[CRenderTarget::PopAxisAlignedClip](../Topic/CRenderTarget::PopAxisAlignedClip.md)|已從轉譯目標中移除最後一個與軸對齊的裁剪。  呼叫這個方法後，裁剪將不再套用至後續的繪製作業。|  
|[CRenderTarget::PopLayer](../Topic/CRenderTarget::PopLayer.md)|停止將繪製作業重新導向至最後一個 PushLayer 呼叫指定的圖層。|  
|[CRenderTarget::PushAxisAlignedClip](../Topic/CRenderTarget::PushAxisAlignedClip.md)|已從轉譯目標中移除最後一個與軸對齊的裁剪。  呼叫這個方法後，裁剪將不再套用至後續的繪製作業。|  
|[CRenderTarget::PushLayer](../Topic/CRenderTarget::PushLayer.md)|將指定的圖層加入至轉譯目標，讓它接收所有後續的繪製作業，直到呼叫 PopLayer 為止。|  
|[CRenderTarget::RestoreDrawingState](../Topic/CRenderTarget::RestoreDrawingState.md)|將轉譯目標的繪圖狀態設定為指定之 ID2D1DrawingStateBlock 的繪圖狀態。|  
|[CRenderTarget::SaveDrawingState](../Topic/CRenderTarget::SaveDrawingState.md)|將目前的繪圖狀態儲存到指定的 ID2D1DrawingStateBlock 中。|  
|[CRenderTarget::SetAntialiasMode](../Topic/CRenderTarget::SetAntialiasMode.md)|設定轉譯目標的消除鋸齒模式。  消除鋸齒模式會套用至所有的後續繪製作業，不包括文字及字符繪製作業。|  
|[CRenderTarget::SetDpi](../Topic/CRenderTarget::SetDpi.md)|設定轉譯目標的 Dots Per Inch \(DPI\)。|  
|[CRenderTarget::SetTags](../Topic/CRenderTarget::SetTags.md)|指定後續繪製作業的標籤。|  
|[CRenderTarget::SetTextAntialiasMode](../Topic/CRenderTarget::SetTextAntialiasMode.md)|指定要用於後續文字及字符繪製作業的消除鋸齒模式。|  
|[CRenderTarget::SetTextRenderingParams](../Topic/CRenderTarget::SetTextRenderingParams.md)|指定要套用至所有後續文字及字符繪製作業的文字呈現選項。|  
|[CRenderTarget::SetTransform](../Topic/CRenderTarget::SetTransform.md)|多載。  將指定的轉換套用至轉譯目標，並取代現有的轉換。  所有後續的繪製作業都會在轉換的空間中發生。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CRenderTarget::VerifyResource](../Topic/CRenderTarget::VerifyResource.md)|驗證 CD2DResource 物件有效性，如果物件尚不存在，則建立該物件。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CRenderTarget::operator ID2D1RenderTarget\*](../Topic/CRenderTarget::operator%20ID2D1RenderTarget*.md)|傳回 ID2D1RenderTarget 介面|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CRenderTarget::m\_lstResources](../Topic/CRenderTarget::m_lstResources.md)|CD2DResource 物件指標的清單。|  
|[CRenderTarget::m\_pRenderTarget](../Topic/CRenderTarget::m_pRenderTarget.md)|ID2D1RenderTarget 物件的指標。|  
|[CRenderTarget::m\_pTextFormatDefault](../Topic/CRenderTarget::m_pTextFormatDefault.md)|包含預設文字格式的 CD2DTextFormat 物件的指標。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)