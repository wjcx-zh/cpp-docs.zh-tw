---
title: "CMFCToolBarImages Class | Microsoft Docs"
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
  - "CMFCToolBarImages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarImages class"
ms.assetid: d4e50518-9ffc-406f-9996-f79e5cd38155
caps.latest.revision: 31
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCToolBarImages Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在工具列上的影像。  `CMFCToolBarImages` 類別處理從檔案載入的應用程式資源或工具列影像。  
  
## 語法  
  
```  
class CMFCToolBarImages : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarImages::CMFCToolBarImages](../Topic/CMFCToolBarImages::CMFCToolBarImages.md)|建構 `CMFCToolBarImages` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarImages::AdaptColors](../Topic/CMFCToolBarImages::AdaptColors.md)||  
|[CMFCToolBarImages::AddIcon](../Topic/CMFCToolBarImages::AddIcon.md)|將圖示加入工具列影像。|  
|[CMFCToolBarImages::AddImage](../Topic/CMFCToolBarImages::AddImage.md)|將點陣圖為工具列影像。|  
|[CMFCToolBarImages::CleanUp](../Topic/CMFCToolBarImages::CleanUp.md)||  
|[CMFCToolBarImages::Clear](../Topic/CMFCToolBarImages::Clear.md)|釋放配置給這個物件相關聯的系統資源。|  
|[CMFCToolBarImages::ConvertTo32Bits](../Topic/CMFCToolBarImages::ConvertTo32Bits.md)|轉換為 32 bpp 影像中加底線的點陣圖。|  
|[CMFCToolBarImages::CopyImageToClipboard](../Topic/CMFCToolBarImages::CopyImageToClipboard.md)||  
|[CMFCToolBarImages::CopyTo](../Topic/CMFCToolBarImages::CopyTo.md)||  
|[CMFCToolBarImages::CreateFromImageList](../Topic/CMFCToolBarImages::CreateFromImageList.md)|初始化從影像清單 \([CImageList Class](../../mfc/reference/cimagelist-class.md)\) 的工具列影像。|  
|[CMFCToolBarImages::CreateRegionFromImage](../Topic/CMFCToolBarImages::CreateRegionFromImage.md)||  
|[CMFCToolBarImages::DeleteImage](../Topic/CMFCToolBarImages::DeleteImage.md)|移除具有從工具列影像之指定的索引處影像，如果這組工具列影像包含使用者定義的影像。|  
|[CMFCToolBarImages::Draw](../Topic/CMFCToolBarImages::Draw.md)|繪製單一工具列影像 \(按鈕\)。|  
|[CMFCToolBarImages::DrawEx](../Topic/CMFCToolBarImages::DrawEx.md)||  
|[CMFCToolBarImages::EnableRTL](../Topic/CMFCToolBarImages::EnableRTL.md)||  
|[CMFCToolBarImages::EndDrawImage](../Topic/CMFCToolBarImages::EndDrawImage.md)|要在其中繪製之後，以釋放系統資源工具列影像。|  
|[CMFCToolBarImages::ExtractIcon](../Topic/CMFCToolBarImages::ExtractIcon.md)|傳回具有從工具列影像來繪製指定的影像索引的圖示。|  
|[CMFCToolBarImages::FillDitheredRect](../Topic/CMFCToolBarImages::FillDitheredRect.md)|填滿矩形使用工具列背景色彩的筆刷。|  
|[CMFCToolBarImages::GetAlwaysLight](../Topic/CMFCToolBarImages::GetAlwaysLight.md)||  
|[CMFCToolBarImages::GetBitsPerPixel](../Topic/CMFCToolBarImages::GetBitsPerPixel.md)|傳回底線的影像的目前解析度。|  
|[CMFCToolBarImages::GetCount](../Topic/CMFCToolBarImages::GetCount.md)|傳回影像的數目會在工具列上的。|  
|[CMFCToolBarImages::GetDisabledImageAlpha](../Topic/CMFCToolBarImages::GetDisabledImageAlpha.md)|傳回為停用影像使用的 Alpha 色頻值。|  
|[CMFCToolBarImages::GetFadedImageAlpha](../Topic/CMFCToolBarImages::GetFadedImageAlpha.md)||  
|[CMFCToolBarImages::GetImageSize](../Topic/CMFCToolBarImages::GetImageSize.md)|擷取或記憶體中的工具列上的影像大小 \(來源大小\) 儲存，或是螢幕工具列上的影像大小 \(目的大小\) 繪製。|  
|[CMFCToolBarImages::GetImageWell](../Topic/CMFCToolBarImages::GetImageWell.md)|將控制代碼傳回給包含所有工具列影像的點陣圖。|  
|[CMFCToolBarImages::GetImageWellLight](../Topic/CMFCToolBarImages::GetImageWellLight.md)||  
|[CMFCToolBarImages::GetLastImageRect](../Topic/CMFCToolBarImages::GetLastImageRect.md)||  
|[CMFCToolBarImages::GetLightPercentage](../Topic/CMFCToolBarImages::GetLightPercentage.md)||  
|[CMFCToolBarImages::GetMapTo3DColors](../Topic/CMFCToolBarImages::GetMapTo3DColors.md)||  
|[CMFCToolBarImages::GetMask](../Topic/CMFCToolBarImages::GetMask.md)||  
|[CMFCToolBarImages::GetResourceOffset](../Topic/CMFCToolBarImages::GetResourceOffset.md)|傳回指定的資源 ID. 的影像索引。|  
|[CMFCToolBarImages::GetScale](../Topic/CMFCToolBarImages::GetScale.md)|傳回底線的影像目前的縮放比例。|  
|[CMFCToolBarImages::GetTransparentColor](../Topic/CMFCToolBarImages::GetTransparentColor.md)||  
|[CMFCToolBarImages::GrayImages](../Topic/CMFCToolBarImages::GrayImages.md)|灰色使其外觀的工具列影像停用。|  
|[CMFCToolBarImages::Is32BitTransparencySupported](../Topic/CMFCToolBarImages::Is32BitTransparencySupported.md)|判斷作業系統是否支援 32 位元的 Alpha 混色。|  
|[CMFCToolBarImages::IsPreMultiplyAutoCheck](../Topic/CMFCToolBarImages::IsPreMultiplyAutoCheck.md)||  
|[CMFCToolBarImages::IsRTL](../Topic/CMFCToolBarImages::IsRTL.md)|判斷從右至左 \(RTL\) 支援是否已啟用。|  
|[CMFCToolBarImages::IsReadOnly](../Topic/CMFCToolBarImages::IsReadOnly.md)|決定工具列影像是否為唯讀。|  
|[CMFCToolBarImages::IsScaled](../Topic/CMFCToolBarImages::IsScaled.md)|告知是否加上底線的影像會縮放。|  
|[CMFCToolBarImages::IsUserImagesList](../Topic/CMFCToolBarImages::IsUserImagesList.md)|判斷這個集合工具列影像是否包含使用者定義的影像。|  
|[CMFCToolBarImages::IsValid](../Topic/CMFCToolBarImages::IsValid.md)|判斷這個集合工具列影像是否包含有效的工具列影像。|  
|[CMFCToolBarImages::Load](../Topic/CMFCToolBarImages::Load.md)|載入工具列影像從系統資源或從檔案。|  
|[CMFCToolBarImages::LoadStr](../Topic/CMFCToolBarImages::LoadStr.md)||  
|[CMFCToolBarImages::MapFromSysColor](../Topic/CMFCToolBarImages::MapFromSysColor.md)||  
|[CMFCToolBarImages::MapTo3dColors](../Topic/CMFCToolBarImages::MapTo3dColors.md)||  
|[CMFCToolBarImages::MapToSysColor](../Topic/CMFCToolBarImages::MapToSysColor.md)||  
|[CMFCToolBarImages::MapToSysColorAlpha](../Topic/CMFCToolBarImages::MapToSysColorAlpha.md)||  
|[CMFCToolBarImages::Mirror](../Topic/CMFCToolBarImages::Mirror.md)|水平反映所有工具列影像。|  
|[CMFCToolBarImages::MirrorBitmap](../Topic/CMFCToolBarImages::MirrorBitmap.md)|水平反映點陣圖。|  
|[CMFCToolBarImages::MirrorBitmapVert](../Topic/CMFCToolBarImages::MirrorBitmapVert.md)||  
|[CMFCToolBarImages::MirrorVert](../Topic/CMFCToolBarImages::MirrorVert.md)||  
|[CMFCToolBarImages::OnSysColorChange](../Topic/CMFCToolBarImages::OnSysColorChange.md)||  
|[CMFCToolBarImages::PrepareDrawImage](../Topic/CMFCToolBarImages::PrepareDrawImage.md)|配置要求繪製工具列影像在指定大小的資源。|  
|[CMFCToolBarImages::Save](../Topic/CMFCToolBarImages::Save.md)|如果這組工具列影像包含使用者定義的影像，在檔案中儲存工具列影像。|  
|[CMFCToolBarImages::SetAlwaysLight](../Topic/CMFCToolBarImages::SetAlwaysLight.md)||  
|[CMFCToolBarImages::SetDisabledImageAlpha](../Topic/CMFCToolBarImages::SetDisabledImageAlpha.md)|設定為停用影像使用的 Alpha 色頻值。|  
|[CMFCToolBarImages::SetFadedImageAlpha](../Topic/CMFCToolBarImages::SetFadedImageAlpha.md)||  
|[CMFCToolBarImages::SetImageSize](../Topic/CMFCToolBarImages::SetImageSize.md)|將工具列影像大小 \(來源\) 的大小。|  
|[CMFCToolBarImages::SetLightPercentage](../Topic/CMFCToolBarImages::SetLightPercentage.md)||  
|[CMFCToolBarImages::SetMapTo3DColors](../Topic/CMFCToolBarImages::SetMapTo3DColors.md)||  
|[CMFCToolBarImages::SetPreMultiplyAutoCheck](../Topic/CMFCToolBarImages::SetPreMultiplyAutoCheck.md)||  
|[CMFCToolBarImages::SetSingleImage](../Topic/CMFCToolBarImages::SetSingleImage.md)||  
|[CMFCToolBarImages::SetTransparentColor](../Topic/CMFCToolBarImages::SetTransparentColor.md)|將工具列影像透明色彩。|  
|[CMFCToolBarImages::SmoothResize](../Topic/CMFCToolBarImages::SmoothResize.md)|成功地調整大小加上底線的影像。|  
|[CMFCToolBarImages::UpdateImage](../Topic/CMFCToolBarImages::UpdateImage.md)|更新從點陣圖之使用者定義的工具列影像。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarImages::PreMultiplyAlpha](../Topic/CMFCToolBarImages::PreMultiplyAlpha.md)||  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCToolBarImages::m\_bDisableTrueColorAlpha](../Topic/CMFCToolBarImages::m_bDisableTrueColorAlpha.md)|`TRUE` ，如果 truecolor Alpha 混色 \(32 位元色彩\) 已停用。|  
  
## 備註  
 工具列影像 Managed 完整點陣圖是由 `CMFCToolbarImages` 的包含一或多個以工具列影像 \(按鈕\) 固定大小。  
  
## 範例  
 您可以使用類別，在 `CMFCToolBarImages` 的各種方法。下列範例將示範如何設定 `CMFCToolBarImages` 物件。  這個範例顯示如何將工具列影像的大小，載入影像，並將影像的透明色彩。  這個程式碼片段是 [Visual Studio 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#32](../../mfc/codesnippet/CPP/cmfctoolbarimages-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#33](../../mfc/codesnippet/CPP/cmfctoolbarimages-class_2.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md)  
  
## 需求  
 **標題:** afxtoolbarimages.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)