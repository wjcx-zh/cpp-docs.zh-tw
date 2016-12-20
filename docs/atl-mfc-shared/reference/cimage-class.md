---
title: "CImage Class | Microsoft Docs"
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
  - "CImage"
  - "ATL.CImage"
  - "ATL::CImage"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".gif 檔案, ATL and MFC support"
  - "點陣圖 [C++], ATL and MFC support for"
  - "CImage class"
  - "GIF 檔, ATL and MFC support"
  - "影像 [C++], ATL and MFC support for"
  - "jpeg 檔案"
  - "PNG 檔案, ATL and MFC support"
  - "transparent color"
ms.assetid: 52861e3d-bf7e-481f-a240-90e88f76c490
caps.latest.revision: 20
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CImage Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在`CImage` JPEG、GIF、BMP 和可攜式網路圖形 \(PNG\) 格式提供增強的點陣圖支援，包括載入和儲存影像。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CImage  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CImage::CImage](../Topic/CImage::CImage.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CImage::AlphaBlend](../Topic/CImage::AlphaBlend.md)|顯示具有透明或半透明的像素的點陣圖。|  
|[CImage::Attach](../Topic/CImage::Attach.md)|`HBITMAP` `CImage` 附加至物件。  可以搭配非 DIB 區段點陣圖或 DIB 區段點陣圖。|  
|[CImage::BitBlt](../Topic/CImage::BitBlt.md)|複製來源裝置內容的點陣圖加入至目前的裝置內容。|  
|[CImage::Create](../Topic/CImage::Create.md)|建立 DIB 區段點陣圖並將其附加至先前 `CImage` 建構的物件。|  
|[CImage::CreateEx](../Topic/CImage::CreateEx.md)|建立 DIB 區段點陣圖 \(利用不同的參數\) 附加至先前建構的 `CImage` 物件。|  
|[CImage::Destroy](../Topic/CImage::Destroy.md)|中斷連結 `CImage` 物件的點陣圖並終結該點陣圖。|  
|[CImage::Detach](../Topic/CImage::Detach.md)|中斷連結 `CImage` 物件的點陣圖。|  
|[CImage::Draw](../Topic/CImage::Draw.md)|複製來源矩形的點陣圖複製到目的矩形。  **繪圖** 自動縮放或壓縮點陣圖 \(如果需要的話，以符合目的端矩形的維度和控制代碼和 alpha 著色和透明色彩。|  
|[CImage::GetBits](../Topic/CImage::GetBits.md)|擷取指標點陣圖的實際像素值。|  
|[CImage::GetBPP](../Topic/CImage::GetBPP.md)|擷取每一像素位元數。|  
|[CImage::GetColorTable](../Topic/CImage::GetColorTable.md)|從輸入範圍在色彩表中擷取紅色，綠色，藍色 \(RGB\) 色彩值。|  
|[CImage::GetDC](../Topic/CImage::GetDC.md)|擷取目前點陣圖選取到裝置內容的。|  
|[CImage::GetExporterFilterString](../Topic/CImage::GetExporterFilterString.md)|尋找可用的影像格式和其說明。|  
|[CImage::GetHeight](../Topic/CImage::GetHeight.md)|擷取目前影像的高度 \(以像素為單位\)。|  
|[CImage::GetImporterFilterString](../Topic/CImage::GetImporterFilterString.md)|尋找可用的影像格式和其說明。|  
|[CImage::GetMaxColorTableEntries](../Topic/CImage::GetMaxColorTableEntries.md)|在色彩表中擷取項目的最大數目。|  
|[CImage::GetPitch](../Topic/CImage::GetPitch.md)|擷取目前影像的字幅，以位元組為單位\)。|  
|[CImage::GetPixel](../Topic/CImage::GetPixel.md)|擷取 *x* 和 *y.*指定像素的色彩。|  
|[CImage::GetPixelAddress](../Topic/CImage::GetPixelAddress.md)|擷取指定像素的位址。|  
|[CImage::GetTransparentColor](../Topic/CImage::GetTransparentColor.md)|擷取透明色彩的位置在色彩表中。|  
|[CImage::GetWidth](../Topic/CImage::GetWidth.md)|擷取目前影像的寬度 \(以像素為單位\)。|  
|[CImage::IsDIBSection](../Topic/CImage::IsDIBSection.md)|判斷附加的點陣圖是否為 DIB 部分。|  
|[CImage::IsIndexed](../Topic/CImage::IsIndexed.md)|表示點陣圖的色彩對應至索引的調色盤。|  
|[CImage::IsNull](../Topic/CImage::IsNull.md)|表示來源點陣圖目前是否已載入。|  
|[CImage::IsTransparencySupported](../Topic/CImage::IsTransparencySupported.md)|指出應用程式是否支援透明點陣圖和在 Windows 2000 \(含\) 以後版本編譯。|  
|[CImage::Load](../Topic/CImage::Load.md)|從指定的檔案載入影像。|  
|[CImage::LoadFromResource](../Topic/CImage::LoadFromResource.md)|從指定的資源載入影像。|  
|[CImage::MaskBlt](../Topic/CImage::MaskBlt.md)|使用指定的遮罩和光柵作業 \(Raster，合併色彩資料來源和目的點陣圖。|  
|[CImage::PlgBlt](../Topic/CImage::PlgBlt.md)|在來源裝置內容執行從矩形的位元區塊傳輸至平行四邊形在目的裝置内容。|  
|[CImage::ReleaseDC](../Topic/CImage::ReleaseDC.md)|釋放所使用的 [CImage::GetDC](../Topic/CImage::GetDC.md)擷取裝置內容。|  
|[CImage::ReleaseGDIPlus](../Topic/CImage::ReleaseGDIPlus.md)|釋放 GDI\+ 所使用的資源。  必須呼叫以釋放全域 `CImage` 物件所建立的資源。|  
|[CImage::Save](../Topic/CImage::Save.md)|將影像，則指定的型別。  \[**儲存**\] 無法指定影像選項。|  
|[CImage::SetColorTable](../Topic/CImage::SetColorTable.md)|在部分 DIB 的色彩表中設定項目的範圍中顯示為紅色，綠色，藍色\) RGB 色彩值。|  
|[CImage::SetPixel](../Topic/CImage::SetPixel.md)|設定為在指定的座標轉換為指定的色彩。|  
|[CImage::SetPixelIndexed](../Topic/CImage::SetPixelIndexed.md)|設定為在指定的座標對應至色彩\] 調色盤中的指定索引處的。|  
|[CImage::SetPixelRGB](../Topic/CImage::SetPixelRGB.md)|設定為在指定的座標轉換為指定的紅色，綠色，藍色 \(RGB\) 值。|  
|[CImage::SetTransparentColor](../Topic/CImage::SetTransparentColor.md)|設定會被視為透明的色彩索引。  只有在調色盤色彩可以是透明的。|  
|[CImage::StretchBlt](../Topic/CImage::StretchBlt.md)|複製來源矩形的點陣圖的目的矩形，自動縮放或壓縮點陣圖至適合目的矩形的維度，如果需要。|  
|[CImage::TransparentBlt](../Topic/CImage::TransparentBlt.md)|複製具有透明色彩的點陣圖來源裝置內容加入至目前的裝置內容。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CImage::operator HBITMAP](../Topic/CImage::operator%20HBITMAP.md)|傳回視窗控制代碼 `CImage` 附加至物件。|  
  
## 備註  
 `CImage` 採用與裝置無關的點陣圖 \(DIB\) 部分的點陣圖，不過，您可以使用 [建立](../Topic/CImage::Create.md) 或 [CImage::Load](../Topic/CImage::Load.md) 只 DIB 部分。  使用 [連結](../Topic/CImage::Attach.md)，您可以將非 DIB 區段點陣圖儲存至 `CImage` 物件，另一方面，但您不可以使用下列方法， `CImage` 支援 DIB 部分點陣圖:  
  
-   [GetBits](../Topic/CImage::GetBits.md)  
  
-   [GetColorTable](../Topic/CImage::GetColorTable.md)  
  
-   [GetMaxColorTableEntries](../Topic/CImage::GetMaxColorTableEntries.md)  
  
-   [GetPitch](../Topic/CImage::GetPitch.md)  
  
-   [GetPixelAddress](../Topic/CImage::GetPixelAddress.md)  
  
-   [IsIndexed](../Topic/CImage::IsIndexed.md)  
  
-   [SetColorTable](../Topic/CImage::SetColorTable.md)  
  
 若要判斷已附加的點陣圖是否為 DIB 區段，請呼叫 [IsDibSection](../Topic/CImage::IsDIBSection.md)**.**  
  
> [!NOTE]
>  在 Visual Studio .NET 2003. 的**Note** ，這個類別會保持 `CImage` 物件數目的計數建立。  當計數成為 0 中，函式 [GdiplusShutdown](_gdiplus_func_gdiplusshutdown_) 自動呼叫釋放 GDI\+ 所使用的資源。  這可確保正確直接或間接地終結 DLL 建立的所有 `CImage` 物件，並 **GdiplusShutdown** 沒有從 `DllMain`呼叫。  
  
> [!NOTE]
>  使用全域 `CImage` 不建議在 DLL 的物件。  如果您在 DLL 必須使用全域 `CImage` 物件，呼叫明確釋放的 [CImage::ReleaseGDIPlus](../Topic/CImage::ReleaseGDIPlus.md) 資源使用由 GDI\+。  
  
 `CImage` 無法被選取到新的 [CDC](../../mfc/reference/cdc-class.md)。  `CImage` 建立該影像的 **HDC** 。  由於 `HBITMAP` 可以一次只能選取到一 **HDC** ， `HBITMAP` 與 `CImage` 無法被選取到另一 **HDC**。  如果您需要 `CDC`，從 `CImage` 中擷取 **HDC** 並將它 [CDC::FromHandle](../Topic/CDC::FromHandle.md)。  
  
## 範例  
 [!code-cpp[NVC_ATLMFC_Utilities#70](../../atl-mfc-shared/codesnippet/CPP/cimage-class_1.cpp)]  
  
 當您在 MFC 專案時使用 `CImage` ，請注意在專案中的哪些成員函式需要一個指標 [CBitmap](../../mfc/reference/cbitmap-class.md) 物件。  如果您要使用這類的函式的 `CImage` ，就像 [CMenu::AppendMenu](../Topic/CMenu::AppendMenu.md)，使用 [CBitmap::FromHandle](../Topic/CBitmap::FromHandle.md)，將您的 `CImage``HBITMAP`和使用傳回的 `CBitmap*`。  
  
## 範例  
 [!code-cpp[NVC_ATLMFC_Utilities#71](../../atl-mfc-shared/codesnippet/CPP/cimage-class_2.cpp)]  
  
 藉由 `CImage`，可以存取 DIB 區段的實際欄位的。  您可以使用物件 `CImage` 任何先前使用一個 Win32 HBITMAP 或 DIB 部分。  
  
> [!NOTE]
>  下列 `CImage` 方法有使用的限制:  
  
|方法|限制|  
|--------|--------|  
|[PlgBlt](../Topic/CImage::PlgBlt.md)|只有 Windows NT 4.0 \(含\) 以後版本上執行。  在執行 Windows 95 \/98 \(含\) 以後版本的應用程式將無法運作。|  
|[MaskBlt](../Topic/CImage::MaskBlt.md)|只有 Windows NT 4.0 \(含\) 以後版本上執行。  在執行 Windows 95 \/98 \(含\) 以後版本的應用程式將無法運作。|  
|[AlphaBlend](../Topic/CImage::AlphaBlend.md)|只有 Windows 2000、Windows 98 和更新系統搭配使用。|  
|[TransparentBlt](../Topic/CImage::TransparentBlt.md)|只有 Windows 2000、Windows 98 和更新系統搭配使用。|  
|[繪圖](../Topic/CImage::Draw.md)|支援以 Windows 2000、Windows 98 和只更新系統的透明度。|  
  
 請參閱 [與舊版作業系統的 CImage 限制](../../mfc/cimage-limitations-with-earlier-operating-systems.md) 如需這些方法的限制的詳細資訊。  
  
 您可以使用從 MFC 或 ATL 中 `CImage` 。  
  
> [!NOTE]
>  使用 `CImage`時，會在您建置專案，您必須定義 `CString` ，才能加入 `atlimage.h`之前。  如果您的專案使用 ATL，而不使用 MFC，包含 `atlstr.h` ，才能加入 `atlimage.h`之前。  如果您的專案使用 MFC \(，如果它是一個 ATL 專案具有 MFC 支援\)，包含 `afxstr.h` ，才能加入 `atlimage.h`之前。  
>   
>  同樣地，，才能加入 `atlimpl.cpp`之前，您必須包含 `atlimage.h` 。  若要輕鬆地達成這個目的，請 `atlimage.h` 包括在您的 `stdafx.h`。  
  
## 需求  
 **Header:** atlimage.h  
  
## 請參閱  
 [MMXSwarm 範例](../../top/visual-cpp-samples.md)   
 [SimpleImage 範例](../../top/visual-cpp-samples.md)   
 [Device\-Independent Bitmaps](http://msdn.microsoft.com/library/windows/desktop/dd183562)   
 [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183494)   
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)