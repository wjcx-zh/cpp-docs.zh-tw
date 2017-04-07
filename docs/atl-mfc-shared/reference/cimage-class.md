---
title: "CImage 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CImage
- ATLIMAGE/ATL::CImage
- ATLIMAGE/ATL::CImage::CImage
- ATLIMAGE/ATL::CImage::AlphaBlend
- ATLIMAGE/ATL::CImage::Attach
- ATLIMAGE/ATL::CImage::BitBlt
- ATLIMAGE/ATL::CImage::Create
- ATLIMAGE/ATL::CImage::CreateEx
- ATLIMAGE/ATL::CImage::Destroy
- ATLIMAGE/ATL::CImage::Detach
- ATLIMAGE/ATL::CImage::Draw
- ATLIMAGE/ATL::CImage::GetBits
- ATLIMAGE/ATL::CImage::GetBPP
- ATLIMAGE/ATL::CImage::GetColorTable
- ATLIMAGE/ATL::CImage::GetDC
- ATLIMAGE/ATL::CImage::GetExporterFilterString
- ATLIMAGE/ATL::CImage::GetHeight
- ATLIMAGE/ATL::CImage::GetImporterFilterString
- ATLIMAGE/ATL::CImage::GetMaxColorTableEntries
- ATLIMAGE/ATL::CImage::GetPitch
- ATLIMAGE/ATL::CImage::GetPixel
- ATLIMAGE/ATL::CImage::GetPixelAddress
- ATLIMAGE/ATL::CImage::GetTransparentColor
- ATLIMAGE/ATL::CImage::GetWidth
- ATLIMAGE/ATL::CImage::IsDIBSection
- ATLIMAGE/ATL::CImage::IsIndexed
- ATLIMAGE/ATL::CImage::IsNull
- ATLIMAGE/ATL::CImage::IsTransparencySupported
- ATLIMAGE/ATL::CImage::Load
- ATLIMAGE/ATL::CImage::LoadFromResource
- ATLIMAGE/ATL::CImage::MaskBlt
- ATLIMAGE/ATL::CImage::PlgBlt
- ATLIMAGE/ATL::CImage::ReleaseDC
- ATLIMAGE/ATL::CImage::ReleaseGDIPlus
- ATLIMAGE/ATL::CImage::Save
- ATLIMAGE/ATL::CImage::SetColorTable
- ATLIMAGE/ATL::CImage::SetPixel
- ATLIMAGE/ATL::CImage::SetPixelIndexed
- ATLIMAGE/ATL::CImage::SetPixelRGB
- ATLIMAGE/ATL::CImage::SetTransparentColor
- ATLIMAGE/ATL::CImage::StretchBlt
- ATLIMAGE/ATL::CImage::TransparentBlt
dev_langs:
- C++
helpviewer_keywords:
- jpeg files
- bitmaps [C++], ATL and MFC support for
- images [C++], ATL and MFC support for
- gif files, ATL and MFC support
- .gif files, ATL and MFC support
- PNG files, ATL and MFC support
- CImage class
- transparent color
ms.assetid: 52861e3d-bf7e-481f-a240-90e88f76c490
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: f74e5952401d6f9608425681cd91120b648e7b13
ms.lasthandoff: 02/24/2017

---
# <a name="cimage-class"></a>CImage 類別
`CImage`提供增強的點陣圖支援，包括載入和儲存影像，JPEG、 GIF、 BMP 及可攜式網路圖形 (PNG) 格式的能力。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CImage
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CImage::CImage](#cimage)|建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CImage::AlphaBlend](#alphablend)|顯示具有透明或半透明的像素的點陣圖。|  
|[CImage::Attach](#attach)|附加`HBITMAP`到`CImage`物件。 可以搭配非 DIB 區段點陣圖或 DIB 區段點陣圖。|  
|[CImage::BitBlt](#bitblt)|來源裝置內容的點陣圖複製到這個目前的裝置內容。|  
|[CImage::Create](#create)|DIB 區段點陣圖，並將它附加至先前建構`CImage`物件。|  
|[CImage::CreateEx](#createex)|建立 DIB 區段點陣圖 （與其他參數），並將它附加至先前建構`CImage`物件。|  
|[CImage::Destroy](#destroy)|中斷連結從點陣圖`CImage`物件，並終結點陣圖。|  
|[CImage::Detach](#detach)|中斷連結從點陣圖`CImage`物件。|  
|[Cimage](#draw)|來源矩形的點陣圖複製到目的地矩形。 **繪製**延伸或壓縮點陣圖，以符合目的地矩形的尺寸，如有必要，以及處理 alpha 混色和透明的色彩。|  
|[CImage::GetBits](#getbits)|擷取的點陣圖的實際像素值的指標。|  
|[CImage::GetBPP](#getbpp)|擷取每個像素的位元。|  
|[CImage::GetColorTable](#getcolortable)|從範圍的色彩表中的項目擷取紅色、 綠色、 藍 (RGB) 色彩值。|  
|[CImage::GetDC](#getdc)|擷取裝置內容，其中已選取目前的點陣圖。|  
|[CImage::GetExporterFilterString](#getexporterfilterstring)|尋找可用映像格式，其描述。|  
|[CImage::GetHeight](#getheight)|擷取目前的影像像素為單位的高度。|  
|[CImage::GetImporterFilterString](#getimporterfilterstring)|尋找可用映像格式，其描述。|  
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|擷取色彩表中的項目的數目上限。|  
|[CImage::GetPitch](#getpitch)|擷取目前的映像，以位元組為單位的點數。|  
|[CImage::GetPixel](#getpixel)|擷取指定的像素色彩*x*和*y*。|  
|[CImage::GetPixelAddress](#getpixeladdress)|擷取指定像素的位址。|  
|[CImage::GetTransparentColor](#gettransparentcolor)|擷取的透明色彩的色彩表中的位置。|  
|[CImage::GetWidth](#getwidth)|擷取目前的影像像素為單位的寬度。|  
|[CImage::IsDIBSection](#isdibsection)|決定是否附加的點陣圖 DIB 區段。|  
|[CImage::IsIndexed](#isindexed)|指出點陣圖的色彩會對應至索引的調色盤。|  
|[CImage::IsNull](#isnull)|表示是否目前已載入的來源點陣圖。|  
|[CImage::IsTransparencySupported](#istransparencysupported)|指出應用程式是否支援透明的點陣圖，並已編譯的 Windows 2000 或更新版本。|  
|[CImage::Load](#load)|從指定的檔案載入影像。|  
|[CImage::LoadFromResource](#loadfromresource)|從指定的資源載入影像。|  
|[Maskblt](#maskblt)|結合使用點陣化操作與指定之的遮罩的來源和目的地點陣圖的色彩資料。|  
|[Cimage:: Plgblt](#plgblt)|執行從來源裝置內容中的矩形的位元區塊傳輸，變成平行四邊形在目的地裝置內容中。|  
|[CImage::ReleaseDC](#releasedc)|釋放裝置內容與擷取[CImage::GetDC](#getdc)。|  
|[CImage::ReleaseGDIPlus](#releasegdiplus)|GDI + 所使用的資源釋出。 建立全域的免費資源必須先呼叫`CImage`物件。|  
|[CImage::Save](#save)|將影像儲存為指定的型別。 **儲存**不能指定影像選項。|  
|[CImage::SetColorTable](#setcolortable)|設定紅色、 綠色、 藍色 RGB） 色彩的色彩表之 DIB 區段中的項目範圍中的值。|  
|[CImage::SetPixel](#setpixel)|設定在指定的座標，以指定的色彩的像素。|  
|[CImage::SetPixelIndexed](#setpixelindexed)|設定指定的色彩調色盤的指定索引處的座標處的像素。|  
|[CImage::SetPixelRGB](#setpixelrgb)|設定指定的紅、 綠、 藍 (RGB) 值的指定座標上的像素。|  
|[CImage::SetTransparentColor](#settransparentcolor)|設定透明色彩來進行處理的索引。 只有一種色彩調色盤中的可以是透明的。|  
|[CImage::StretchBlt](#stretchblt)|來源矩形的點陣圖複製到目的地矩形，自動縮放或壓縮點陣圖，以符合目的地矩形的尺寸，如有必要。|  
|[Transparentblt](#transparentblt)|來源裝置內容的透明色彩的點陣圖複製到這個目前的裝置內容。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CImage::operator HBITMAP](#operator_hbitmap)|連接至 Windows 控制代碼傳回`CImage`物件。|  
  
## <a name="remarks"></a>備註  
 `CImage`採用與否，都是與裝置無關點陣圖 (DIB) 區段的點陣圖不過，您可以使用[建立](#create)或[CImage::Load](#load)具有僅 DIB 區段。 您可以將附加至非 DIB 區段點陣圖`CImage`物件使用[附加](#attach)，但是就無法使用下列`CImage`支援 DIB 區段點陣圖的方法︰  
  
- [GetBits](#getbits)  
  
- [GetColorTable](#getcolortable)  
  
- [GetMaxColorTableEntries](#getmaxcolortableentries)  
  
- [GetPitch](#getpitch)  
  
- [GetPixelAddress](#getpixeladdress)  
  
- [IsIndexed](#isindexed)  
  
- [SetColorTable](#setcolortable)  
  
 若要判斷是否附加的點陣圖 DIB 區段，請呼叫[IsDibSection](#isdibsection)**。**  
  
> [!NOTE]
> **請注意**在 Visual Studio.NET 2003 中，這個類別會保留數目的計數`CImage`建立的物件。 每當計數變成 0 時，此函式**GdiplusShutdown**釋放 GDI + 所使用的資源時，會自動呼叫。 這可確保任何`CImage`一定會正確地終結物件直接或間接由 Dll， **GdiplusShutdown**不會從呼叫`DllMain`。  
  
> [!NOTE]
>  使用全域`CImage`不建議在 DLL 中的物件。 如果您需要使用全域`CImage`物件在 DLL 中，呼叫[CImage::ReleaseGDIPlus](#releasegdiplus)明確釋放 GDI + 所使用的資源。  
  
 `CImage`無法選取至新[CDC](../../mfc/reference/cdc-class.md)。 `CImage`建立自己**HDC**映像。 因為`HBITMAP`只能選取成一個**HDC**一次`HBITMAP`聯`CImage`到另一個不能選取**HDC**。 如果您需要`CDC`，擷取**HDC**從`CImage`，並提供給 [CDC::FromHandle] (.../../mfc/reference/cdc-class.md#cdc__fromhandle。  
  
## <a name="example"></a>範例  
```cpp  
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```  
  
 當您使用`CImage`在 MFC 專案中，請注意您的專案中的成員函式預期的指標[CBitmap](../../mfc/reference/cbitmap-class.md)物件。 如果您想要使用`CImage`這類函式，例如[CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)，使用[CBitmap::FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle)，將它傳遞您`CImage` `HBITMAP`，並使用傳回`CBitmap*`。  

  
## <a name="example"></a>範例  
```cpp  
void CMyDlg::OnRButtonDown(UINT nFlags, CPoint point)
{
  UNREFERENCED_PARAMETER(nFlags);

  CBitmap* pBitmap = CBitmap::FromHandle(m_myImage);
  m_pmenuPop->AppendMenu(0, ID_BMPCOMMAND, pBitmap);
  ClientToScreen(&point);
  m_pmenuPop->TrackPopupMenu(TPM_RIGHTBUTTON | TPM_LEFTALIGN, point.x, 
  point.y, this);
}
```  

  
 透過`CImage`，您可以存取之 DIB 區段的實際位元。 您可以使用`CImage`您先前使用的 Win32 HBITMAP 或 DIB 區段的任何位置物件。  
  
> [!NOTE]
>  下列`CImage`方法有其用法的限制︰  
  
|方法|限制|  
|------------|----------------|  
|[PlgBlt](#plgblt)|只有 Windows NT 4.0 或更新版本的運作方式。 無法在執行 Windows 95/98 或更新版本的應用程式。|  
|[MaskBlt](#maskblt)|只有 Windows NT 4.0 或更新版本的運作方式。 無法在執行 Windows 95/98 或更新版本的應用程式。|  
|[Alphablend，還有旁邊](#alphablend)|適用於 Windows 2000、 Windows 98 和更新版本的系統。|  
|[TransparentBlt](#transparentblt)|適用於 Windows 2000、 Windows 98 和更新版本的系統。|  
|[繪製](#draw)|支援與 Windows 2000、 Windows 98 和更新版本的系統的透明度。|  
  
 您可以使用`CImage`從 MFC 或 ATL  
  
> [!NOTE]
>  當您建立的專案使用`CImage`，您必須定義`CString`包含之前`atlimage.h`。 如果您的專案使用 ATL，而非 MFC，包括`atlstr.h`包含之前`atlimage.h`。 如果您的專案使用 MFC （或如果它是 MFC 支援的 ATL 專案），包括`afxstr.h`包含之前`atlimage.h`。  
>   
>  同樣地，您必須包含`atlimage.h`包含之前`atlimpl.cpp`。 若要完成這項作業輕鬆，包括`atlimage.h`中您`stdafx.h`。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlimage.h  
  
##  <a name="alphablend"></a>CImage::AlphaBlend  
 顯示具有透明或半透明的像素的點陣圖。  
  
```
BOOL AlphaBlend(
 HDC hDestDC,
 int xDest,
 int yDest,
 BYTE bSrcAlpha = 0xff,
 BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
 HDC hDestDC,
 const POINT& pointDest,
 BYTE bSrcAlpha = 0xff,
 BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 int xSrc,
 int ySrc,
 int nSrcWidth,
 int nSrcHeight,
 BYTE bSrcAlpha = 0xff,
 BYTE bBlendOp = AC_SRC_OVER);

BOOL AlphaBlend(
 HDC hDestDC,
 const RECT& rectDest,
 const RECT& rectSrc,
 BYTE bSrcAlpha = 0xff,
 BYTE bBlendOp = AC_SRC_OVER);
```  
  
### <a name="parameters"></a>參數  
 `hDestDC`  
 目的地裝置內容的控制代碼。  
  
 `xDest`  
 X 軸座標，以邏輯單位目的矩形左上角。  
  
 `yDest`  
 Y 軸座標，以邏輯單位目的矩形左上角。  
  
 *bSrcAlpha*  
 用於整個來源點陣圖 alpha 透明值。 預設 0xff (255) 假設您的映像不透明，，而且您想要使用僅限每個像素 alpha 值。  
  
 `bBlendOp`  
 Alpha 混色函式的來源和目的地點陣圖、 全域的 alpha 值套用至整個來源點陣圖和來源點陣圖的格式資訊。 來源和目的地 blend 函式是目前僅限於**AC_SRC_OVER**。  
  
 `pointDest`  
 參考[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)識別的邏輯單元的目的矩形左上的角的結構。  
  
 `nDestWidth`  
 以邏輯單位，目的地矩形的寬度。  
  
 `nDestHeight`  
 以邏輯單位，目的地矩形的高度。  
  
 `xSrc`  
 邏輯 x 座標的來源矩形左上角。  
  
 `ySrc`  
 邏輯 y 座標的來源矩形左上角。  
  
 `nSrcWidth`  
 以邏輯單位，來源矩形的寬度。  
  
 `nSrcHeight`  
 以邏輯單位，來源矩形的高度。  
  
 `rectDest`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，用來識別目的地。  
  
 `rectSrc`  
 參考`RECT`結構，來識別來源。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 Alpha 混色點陣圖支援每個像素為基礎的色彩混合。  
  
 當`bBlendOp`設為預設值是**AC_SRC_OVER**，來源點陣圖會透過基礎來源像素的 alpha 值的目的地點陣圖。  

##  <a name="attach"></a>CImage::Attach  
 附加`hBitmap`到`CImage`物件。  
  
```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```  
  
### <a name="parameters"></a>參數  
 `hBitmap`  
 控制代碼`HBITMAP`。  
  
 *eOrientation*  
 指定點陣圖的方向。 可以是下列其中一項：  
  
- **DIBOR_DEFAULT**點陣圖的方向由作業系統決定。 不過，這可能不一定所要的結果在所有作業系統上。 如需詳細資訊，請參閱下列知識庫文件 ( **Q186586**): PRB: GetObject() 一律傳回正數高度的 DIB 區段。  
  
- **DIBOR_BOTTOMUP**點陣圖的線條會以反向順序。 這會導致[CImage::GetBits](#getbits)傳回點陣圖緩衝區結尾附近的指標和[CImage::GetPitch](#getpitch)傳回負數。  
  
- **DIBOR_TOPDOWN**點陣圖的幾行位於最上方往下的順序。 這會導致[CImage::GetBits](#getbits)指標傳回第一個位元組的點陣圖緩衝區和[CImage::GetPitch](#getpitch)傳回正數。  
  
### <a name="remarks"></a>備註  
 可以是點陣圖，非 DIB 區段點陣圖或 DIB 區段點陣圖。 請參閱[IsDIBSection](#isdibsection)只適用於 DIB 的方法清單一節的點陣圖。  
  
##  <a name="bitblt"></a>CImage::BitBlt  
 來源裝置內容的點陣圖複製到這個目前的裝置內容。  
  
```
BOOL BitBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
 HDC hDestDC,
 const POINT& pointDest,
 DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 int xSrc,
 int ySrc,
 DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
 HDC hDestDC,
 const RECT& rectDest,
 const POINT& pointSrc,
 DWORD dwROP = SRCCOPY) const throw();
```  
  
### <a name="parameters"></a>參數  
 `hDestDC`  
 目的地**HDC**。  
  
 `xDest`  
 邏輯 x 座標的目的矩形左上角。  
  
 `yDest`  
 邏輯 y 座標的目的矩形左上角。  
  
 `dwROP`  
 要執行的點陣作業。 點陣作業程式碼會定義如何合併來源、 目的地和模式的位元 （如目前選取的筆刷所定義） 為目的地。 請參閱[BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]其他點陣化操作碼及其描述的清單。  
  
 `pointDest`  
 A[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)結構，表示目的矩形左上的角。  
  
 `nDestWidth`  
 以邏輯單位，目的地矩形的寬度。  
  
 `nDestHeight`  
 以邏輯單位，目的地矩形的高度。  
  
 `xSrc`  
 邏輯 x 座標的來源矩形左上角。  
  
 `ySrc`  
 邏輯 y 座標的來源矩形左上角。  
  
 `rectDest`  
 A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)指出目的地矩形的結構。  
  
 `pointSrc`  
 A**點**結構，表示來源矩形左上的角。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="cimage"></a>CImage::CImage  
 建構 `CImage` 物件。  
  
```
CImage() throw();
```  
  
### <a name="remarks"></a>備註  
 一旦您已建構的物件，呼叫[建立](#create)，[負載](#load)， [LoadFromResource](#loadfromresource)，或[附加](#attach)來附加到物件的點陣圖。  
  
 **請注意**在 Visual Studio 中，這個類別會保留數目的計數`CImage`建立的物件。 每當計數變成 0 時，此函式**GdiplusShutdown**釋放 GDI + 所使用的資源時，會自動呼叫。 這可確保任何`CImage`一定會正確地終結物件直接或間接由 Dll， **GdiplusShutdown**不從 DllMain 呼叫。  
  
 使用全域`CImage`不建議在 DLL 中的物件。 如果您需要使用全域`CImage`物件在 DLL 中，呼叫[CImage::ReleaseGDIPlus](#releasegdiplus)明確釋放 GDI + 所使用的資源。  
  
##  <a name="create"></a>CImage::Create  
 建立`CImage`點陣圖，並將它附加至先前建構`CImage`物件。  
  
```
BOOL Create(
 int nWidth,
 int nHeight,
 int nBPP,
 DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>參數  
 `nWidth`  
 寬度`CImage`點陣圖像素為單位。  
  
 `nHeight`  
 高度`CImage`點陣圖像素為單位。 如果`nHeight`是正數，點陣圖是由下往上 DIB，且其來源，左下的角。 如果`nHeight`是負數，點陣圖是由上而下 DIB 而起源左上的角。  
  
 `nBPP`  
 位元 / 像素的點陣圖中的數字。 通常是 4、 8、 16、 24 或 32。 可以是 1 單色點陣圖或遮罩。  
  
 `dwFlags`  
 指定點陣圖物件是否具有 alpha 色板。 可以是零或多個下列值的組合︰  
  
- **createAlphaChannel**僅適用於如果`nBPP`為 32，和`eCompression`是**BI_RGB**。 如果指定，建立映像會有每個像素，儲存在每個像素 （非字母的 32 位元映像中未使用） 的第 4 個位元組的 alpha （投影片） 值。 呼叫時，會自動使用此 alpha 色頻[CImage::AlphaBlend](#alphablend)。  
  
> [!NOTE]
>  在呼叫[Cimage](#draw)，alpha 色頻的影像會自動 alpha 混色到目的地。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
##  <a name="createex"></a>CImage::CreateEx  
 建立`CImage`點陣圖，並將它附加至先前建構`CImage`物件。  
  
```
BOOL CreateEx(
 int nWidth,
 int nHeight,
 int nBPP,
 DWORD eCompression,
 const DWORD* pdwBitmasks = NULL,
 DWORD dwFlags = 0) throw();
```  
  
### <a name="parameters"></a>參數  
 `nWidth`  
 寬度`CImage`點陣圖像素為單位。  
  
 `nHeight`  
 高度`CImage`點陣圖像素為單位。 如果`nHeight`是正數，點陣圖是由下往上 DIB，且其來源，左下的角。 如果`nHeight`是負數，點陣圖是由上而下 DIB 而起源左上的角。  
  
 `nBPP`  
 位元 / 像素的點陣圖中的數字。 通常是 4、 8、 16、 24 或 32。 可以是 1 單色點陣圖或遮罩。  
  
 `eCompression`  
 指定壓縮由下而上的點陣圖 （Dib 由上而下不能壓縮） 的壓縮的類型。 可為下列其中一個值：  
  
- **BI_RGB**格式未壓縮。 指定這個值時呼叫`CImage::CreateEx`就相當於呼叫`CImage::Create`。  
  
- **BI_BITFIELDS**未壓縮的格式和色彩表包含三個`DWORD`色彩遮罩，指定 [紅色] 綠色，分別和藍色元件，每個像素。 這是在 16 和 32 bpp 點陣圖搭配使用時才有效。  
  
 *pdwBitfields*  
 只有當使用`eCompression`設為**BI_BITFIELDS**，否則必須是**NULL**。 三個陣列的指標`DWORD`位元遮罩，指定每個像素的位元用於紅色、 綠色、 分別和藍色元件、 色彩。 位元欄位的限制相關資訊，請參閱[BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `dwFlags`  
 指定點陣圖物件是否具有 alpha 色板。 可以是零或多個下列值的組合︰  
  
- **createAlphaChannel**僅適用於如果`nBPP`為 32，和`eCompression`是**BI_RGB**。 如果指定，建立映像會有每個像素，儲存在每個像素 （非字母的 32 位元映像中未使用） 的第 4 個位元組的 alpha （投影片） 值。 呼叫時，會自動使用此 alpha 色頻[CImage::AlphaBlend](#alphablend)。  
  
    > [!NOTE]
    >  在呼叫[Cimage](#draw)，alpha 色頻的影像會自動 alpha 混色到目的地。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果成功。 否則**FALSE**。  
  
### <a name="example"></a>範例  
 下列範例會建立 100 x 100 像素點陣圖，使用 16 位元編碼每個像素。 在指定的 16 位元像素位元 0-3 編碼紅元件 4-7 位元編碼綠色和藍色的編碼位元 8-11。 不會使用其餘的 4 個位元。  

```cpp  
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```


##  <a name="destroy"></a>CImage::Destroy  
 中斷連結從點陣圖`CImage`物件，並終結點陣圖。  
  
```
void Destroy() throw();
```  
  
##  <a name="detach"></a>CImage::Detach  
 中斷連結從點陣圖`CImage`物件。  
  
```
HBITMAP Detach() throw();
```  
  
### <a name="return-value"></a>傳回值  
 卸離，點陣圖的控制代碼或**NULL**如果連接不使用任何點陣圖。  
  
##  <a name="draw"></a>Cimage  
 來源裝置內容的點陣圖複製到目前的裝置內容。  
  
```
BOOL Draw(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 int xSrc,
 int ySrc,
 int nSrcWidth,
 int nSrcHeight) const throw();

BOOL Draw(
 HDC hDestDC,
 const RECT& rectDest,
 const RECT& rectSrc) const throw();

BOOL Draw(
 HDC hDestDC,
 int xDest,
 int yDest) const throw();

BOOL Draw(
 HDC hDestDC,
 const POINT& pointDest) const throw();

BOOL Draw(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight) const throw();

BOOL Draw(
 HDC hDestDC,
 const RECT& rectDest) const throw();
```  
  
### <a name="parameters"></a>參數  
 `hDestDC`  
 目的地裝置內容控制代碼。  
  
 `xDest`  
 X 軸座標，以邏輯單位目的矩形左上角。  
  
 `yDest`  
 Y 軸座標，以邏輯單位目的矩形左上角。  
  
 `nDestWidth`  
 以邏輯單位，目的地矩形的寬度。  
  
 `nDestHeight`  
 以邏輯單位，目的地矩形的高度。  
  
 `xSrc`  
 X 座標，以邏輯單位，來源矩形左上角。  
  
 `ySrc`  
 Y 座標，以邏輯單位，來源矩形左上角。  
  
 `nSrcWidth`  
 以邏輯單位，來源矩形的寬度。  
  
 `nSrcHeight`  
 以邏輯單位，來源矩形的高度。  
  
 `rectDest`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，用來識別目的地。  
  
 `rectSrc`  
 參考`RECT`結構，來識別來源。  
  
 `pointDest`  
 參考[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)識別的邏輯單元的目的矩形左上的角的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 **繪製**執行相同的作業[StretchBlt](#stretchblt)，除非您的映像包含透明的色彩或 alpha 色頻。 在此情況下，**繪製**執行相同作業為[TransparentBlt](#transparentblt)或[alphablend，還有旁邊](#alphablend)視需要而定。  
  
 版本**繪製**，不會指定來源矩形，整個來源影像是預設值。 版本的**繪製**未指定目的地矩形的大小、 來源影像的大小是預設值，而且沒有自動縮放或壓縮會發生。  
  
##  <a name="getbits"></a>CImage::GetBits  
 擷取指定的像素點陣圖中的實際位元值的指標。  
  
```
void* GetBits() throw();
```  
  
### <a name="return-value"></a>傳回值  
 點陣圖緩衝區的指標。 如果點陣圖是由下往上 DIB，緩衝區的結尾附近，指標指向。 如果點陣圖是由上而下 DIB，指標會指向第一個位元組的緩衝區。  
  
### <a name="remarks"></a>備註  
 使用這個指標，以及所傳回的值[GetPitch](#getpitch)，您可以找出並變更映像中的個別像素。  
  
> [!NOTE]
>  這個方法支援只有 DIB 區段的點陣圖。因此，您可以存取的像素`CImage`物件相同的方式就像素 DIB 區段。 傳回的指標會指向的位置 （0，0） 像素。  
  
##  <a name="getbpp"></a>CImage::GetBPP  
 擷取每個像素的位元值。  
  
```
int GetBPP() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 每個像素的位元數。  
  
### <a name="remarks"></a>備註  
 這個值會決定定義每個像素的位元數，而在點陣圖中色彩的數目上限。  
  
 每個像素的位元通常是 1、 4、 8、 16、 24 或 32。 請參閱**biBitCount**成員[BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]如需有關此值。  
  
##  <a name="getcolortable"></a>CImage::GetColorTable  
 擷取 DIB 區段的調色盤中的項目範圍中的紅色、 綠色、 藍 (RGB) 色彩值。  
  
```
void GetColorTable(UINT iFirstColor,
 UINT nColors,
 RGBQUAD* prgbColors) const throw();
```  
  
### <a name="parameters"></a>參數  
 `iFirstColor`  
 要擷取之第一個項目的色彩表索引。  
  
 `nColors`  
 若要擷取的色彩表項目數。  
  
 `prgbColors`  
 陣列的指標[RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)結構，以擷取的色彩表項目。  
  
##  <a name="getdc"></a>CImage::GetDC  
 擷取目前已選取成它的映像的裝置內容。  
  
```
HDC GetDC() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 裝置內容的控制代碼。  
  
### <a name="remarks"></a>備註  
 每次呼叫`GetDC`，您必須擁有的後續呼叫[ReleaseDC](#releasedc)。  
  
##  <a name="getexporterfilterstring"></a>CImage::GetExporterFilterString  
 尋找可用的影像格式儲存影像。  
  
```
static HRESULT GetExporterFilterString(CSimpleString& strExporters,
 CSimpleArray<GUID>& aguidFileTypes,
 LPCTSTR pszAllFilesDescription = NULL,
 DWORD dwExclude = excludeDefaultSave,
 TCHAR chSeparator = _T('|'));
```  
  
### <a name="parameters"></a>參數  
 *strExporters*  
 參考**CSimpleString**物件。 請參閱**備註**如需詳細資訊。  
  
 `aguidFileTypes`  
 陣列的 Guid，其中每個元素對應到其中一個字串中的檔案類型。 在範例中`pszAllFilesDescription`， `aguidFileTypes`[0] 是`GUID_NULL`，其餘的陣列值為目前的作業系統所支援的影像檔案格式。  
  
> [!NOTE]
>  如需常數的完整清單，請參閱**影像檔案格式常數**中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `pszAllFilesDescription`  
 如果這個參數不是**NULL**，篩選條件字串，會有一個額外的篩選器清單的開頭。 此篩選條件會有的目前值`pszAllFilesDescription`如它的描述，並接受任何擴充功能清單中的任何其他匯出工具所支援的檔案。  
  
 例如:   

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes, 
 _T("All Image Files"));
```  

  
 `dwExclude`  
 指定要從清單中排除檔案類型的位元旗標集。 允許的旗標如下︰  
  
- **excludeGIF** = 0x01 排除 GIF 檔案。  
  
- **excludeBMP** = 0x02 排除 BMP （Windows 點陣圖） 檔案。  
  
- **excludeEMF** = 0x04，則會排除 EMF （增強型中繼檔） 檔案。  
  
- **excludeWMF** = 0x08 排除 WMF （Windows 中繼檔） 檔案。  
  
- **excludeJPEG** = 0x10 排除 JPEG 檔案。  
  
- **excludePNG** = 0x20 排除 PNG 檔案。  
  
- **excludeTIFF** = 0x40 排除 TIFF 檔案。  
  
- **excludeIcon** = 0x80 排除 ICO （Windows 圖示） 檔。  
  
- **excludeOther** = 0x80000000 排除以上未列出的任何其他檔案類型。  
  
- **excludeDefaultLoad** = 0，表示負載，預設會包含類型的所有檔案  
  
- **excludeDefaultSave** = **excludeIcon | excludeEMF | excludeWMF**儲存，這些檔案會預設排除因為它們通常會有特殊需求。  
  
 `chSeparator`  
 使用映像格式之間的分隔符號。 請參閱**備註**如需詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
### <a name="remarks"></a>備註  
 您可以將產生的格式字串傳遞至您的 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)格式在 [另存新檔] 對話方塊中的物件公開可用映像的檔案副檔名。  
  
 參數*strExporter*格式︰  
  
 檔案 description0 |\*.ext0 | filedescription1 |\*.ext1 |...檔案描述*n*|\*。ext *n*||  
  
 其中 ' |' 所指定的分隔符號字元`chSeparator`。 例如:   
  
 `"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`  
  
 使用預設分隔字元 ' |' 如果您將此字串傳遞給 MFC`CFileDialog`物件。 如果您將此字串傳遞給通用儲存檔案對話方塊中，請使用 null 分隔符號 '\0'。  
  
##  <a name="getheight"></a>CImage::GetHeight  
 擷取的高度，單位為像素的影像。  
  
```
int GetHeight() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 高度，單位為像素的影像。  
  
##  <a name="getimporterfilterstring"></a>CImage::GetImporterFilterString  
 尋找可用的映像格式載入影像。  
  
```
static HRESULT GetImporterFilterString(CSimpleString& strImporters,
 CSimpleArray<GUID>& aguidFileTypes,
 LPCTSTR pszAllFilesDescription = NULL,
 DWORD dwExclude = excludeDefaultLoad,
 TCHAR chSeparator = _T('|'));
```  
  
### <a name="parameters"></a>參數  
 *strImporters*  
 參考**CSimpleString**物件。 請參閱**備註**如需詳細資訊。  
  
 `aguidFileTypes`  
 陣列的 Guid，其中每個元素對應到其中一個字串中的檔案類型。 在範例中`pszAllFilesDescription`， `aguidFileTypes`[0] 是`GUID_NULL`其餘陣列的值為目前的作業系統所支援的影像檔案格式。  
  
> [!NOTE]
>  如需常數的完整清單，請參閱**影像檔案格式常數**中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `pszAllFilesDescription`  
 如果這個參數不是**NULL**，篩選條件字串，會有一個額外的篩選器清單的開頭。 此篩選條件會有的目前值`pszAllFilesDescription`如它的描述，並接受任何擴充功能清單中的任何其他匯出工具所支援的檔案。  
  
 例如:   

```cpp  
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes, 
 _T("All Image Files"));
```  

  
 `dwExclude`  
 指定要從清單中排除檔案類型的位元旗標集。 允許的旗標如下︰  
  
- **excludeGIF** = 0x01 排除 GIF 檔案。  
  
- **excludeBMP** = 0x02 排除 BMP （Windows 點陣圖） 檔案。  
  
- **excludeEMF** = 0x04，則會排除 EMF （增強型中繼檔） 檔案。  
  
- **excludeWMF** = 0x08 排除 WMF （Windows 中繼檔） 檔案。  
  
- **excludeJPEG** = 0x10 排除 JPEG 檔案。  
  
- **excludePNG** = 0x20 排除 PNG 檔案。  
  
- **excludeTIFF** = 0x40 排除 TIFF 檔案。  
  
- **excludeIcon** = 0x80 排除 ICO （Windows 圖示） 檔。  
  
- **excludeOther** = 0x80000000 排除以上未列出的任何其他檔案類型。  
  
- **excludeDefaultLoad** = 0，表示負載，預設會包含類型的所有檔案  
  
- **excludeDefaultSave** = **excludeIcon | excludeEMF | excludeWMF**儲存，這些檔案會預設排除因為它們通常會有特殊需求。  
  
 `chSeparator`  
 使用映像格式之間的分隔符號。 請參閱**備註**如需詳細資訊。  
  
### <a name="remarks"></a>備註  
 您可以將產生的格式字串傳遞至您的 MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)格式中的物件公開可用映像的檔案副檔名**開啟舊檔**對話方塊。  
  
 參數*strImporter*格式︰  
  
 檔案 description0 |\*.ext0 | filedescription1 |\*.ext1 |...檔案描述*n*|\*。ext *n*||  
  
 其中 ' |' 所指定的分隔符號字元`chSeparator`。 例如:   
  
 `"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`  
  
 使用預設分隔字元 ' |' 如果您將此字串傳遞給 MFC`CFileDialog`物件。 如果您將此字串傳遞給一般使用 null 分隔符號 '\0'**開啟舊檔**對話方塊。  
  
##  <a name="getmaxcolortableentries"></a>CImage::GetMaxColorTableEntries  
 擷取色彩表中的項目的數目上限。  
  
```
int GetMaxColorTableEntries() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 色彩表中的項目數目。  
  
### <a name="remarks"></a>備註  
 這個方法支援 DIB 區段點陣圖。  
  
##  <a name="getpitch"></a>CImage::GetPitch  
 擷取映像的點數。  
  
```
int GetPitch() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 映像的字幅。 如果傳回值為負數，點陣圖是由下而上 DIB 而起源左下的角。 如果傳回值是正數，點陣圖是由上而下 DIB 而起源左上的角。  
  
### <a name="remarks"></a>備註  
 推銷是以位元組為單位，表示點陣圖中的一行開頭的兩個記憶體位址和下一步點陣圖一行的開頭之間的距離。 行距以位元組為單位，因為映像的音調可協助您判斷像素格式。 越大，音調也可以包含額外的記憶體，保留的點陣圖。  
  
 使用`GetPitch`與[GetBits](#getbits)來尋找個別像素的影像。  
  
> [!NOTE]
>  這個方法支援 DIB 區段點陣圖。  
  
##  <a name="getpixel"></a>CImage::GetPixel  
 擷取指定位置的像素色彩*x*和*y*。  
  
```
COLORREF GetPixel(int x,int y) const throw();
```  
  
### <a name="parameters"></a>參數  
 *x*  
 像素 x 軸座標。  
  
 *y*  
 像素的 y 座標。  
  
### <a name="return-value"></a>傳回值  
 像素的紅色、 綠色、 藍 (RGB) 值。 如果像素超出了目前裁剪區域，傳回的值是**CLR_INVALID**。  
  
##  <a name="getpixeladdress"></a>CImage::GetPixelAddress  
 擷取像素的確切的位址。  
  
```
void* GetPixelAddress(int x,int y) throw();
```  
  
### <a name="parameters"></a>參數  
 *x*  
 像素 x 軸座標。  
  
 *y*  
 像素的 y 座標。  
  
### <a name="remarks"></a>備註  
 位址是根據來決定的像素座標、 點陣圖和每像素的位元的點數。  
  
 對於小於每像素 8 個位元的格式，這個方法會傳回包含像素的位元組的位址。 例如，如果您的映像格式具有每像素 4 個位元`GetPixelAddress`傳回第一個位元組，而且像素的位址必須計算每個位元組的 2 個像素。  
  
> [!NOTE]
>  這個方法支援 DIB 區段點陣圖。  
  
##  <a name="gettransparentcolor"></a>CImage::GetTransparentColor  
 擷取的透明色彩調色盤中的索引的位置。  
  
```
LONG GetTransparentColor() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 透明的色彩索引。  
  
##  <a name="getwidth"></a>CImage::GetWidth  
 擷取的寬度，單位為像素的影像。  
  
```
int GetWidth() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 點陣圖，單位為像素的寬度。  
  
##  <a name="isdibsection"></a>CImage::IsDIBSection  
 決定是否附加的點陣圖 DIB 區段。  
  
```
bool IsDIBSection() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 **true**如果附加的點陣圖 DIB 區段。 否則**false**。  
  
### <a name="remarks"></a>備註  
 如果點陣圖不 DIB 區段，您不能使用下列`CImage`支援 DIB 區段點陣圖的方法︰  
  
- [GetBits](#getbits)  
  
- [GetColorTable](#getcolortable)  
  
- [GetMaxColorTableEntries](#getmaxcolortableentries)  
  
- [GetPitch](#getpitch)  
  
- [GetPixelAddress](#getpixeladdress)  
  
- [IsIndexed](#isindexed)  
  
- [SetColorTable](#setcolortable)  
  
##  <a name="isindexed"></a>CImage::IsIndexed  
 決定是否點陣圖的像素會對應到調色盤的色彩。  
  
```
bool IsIndexed() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 **true**有索引，否則**false**。  
  
### <a name="remarks"></a>備註  
 這個方法會傳回**true**只有點陣圖是 8 位元 （256 色彩） 或更少。  
  
> [!NOTE]
>  這個方法支援 DIB 區段點陣圖。  
  
##  <a name="isnull"></a>CImage::IsNull  
 決定是否目前已載入的點陣圖。  
  
```
bool IsNull() const throw();
```  
  
### <a name="remarks"></a>備註  
 這個方法會傳回**True**點陣圖目前未載入，否則如果**False**。  
  
##  <a name="istransparencysupported"></a>CImage::IsTransparencySupported  
 指出應用程式是否支援透明的點陣圖，並已編譯的 Windows 2000 或更新版本。  
  
```
static BOOL IsTransparencySupported() throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果目前的平台支援透明度為非零。 否則為 0。  
  
### <a name="remarks"></a>備註  
 如果傳回值是零，且支援透明度，則呼叫[alphablend，還有旁邊](#alphablend)， [TransparentBlt](#transparentblt)，或[繪製](#draw)處理透明色彩。  
  
 如果應用程式編譯時與作業系統搭配使用之前 Windows 2000 或 Windows 98，這個方法一定會傳回 0，即使在較新的作業系統上。  
  

##  <a name="load"></a>CImage::Load  
 載入影像。  
  
```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>參數  
 `pszFileName`  
 包含要載入的影像檔名稱的字串指標。  
  
 `pStream`  
 包含要載入的影像檔名稱的資料流的指標。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
### <a name="remarks"></a>備註  
 載入所指定的影像*pszFileName*或`pStream`。  
  
 有效的影像類型為 BMP、 GIF、 JPEG、 PNG 及 TIFF。  
  
##  <a name="loadfromresource"></a>CImage::LoadFromResource  
 載入的映像，`BITMAP`資源。  
  
```
void LoadFromResource(
 HINSTANCE hInstance,
 LPCTSTR pszResourceName) throw();

void LoadFromResource(
 HINSTANCE hInstance,
 UINT nIDResource) throw();
```  
  
### <a name="parameters"></a>參數  
 `hInstance`  
 包含要載入的映像之模組的執行個體的控制代碼。  
  
 `pszResourceName`  
 包含資源，包含要載入的影像名稱的字串指標。  
  
 `nIDResource`  
 要載入的資源識別碼。  
  
### <a name="remarks"></a>備註  
 資源必須是型別`BITMAP`。  
  
##  <a name="maskblt"></a>Maskblt  
 結合使用點陣化操作與指定之的遮罩的來源和目的地點陣圖的色彩資料。  
  
```
BOOL MaskBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 int xSrc,
 int ySrc,
 HBITMAP hbmMask,
 int xMask,
 int yMask,
 DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
 HDC hDestDC,
 const RECT& rectDest,
 const POINT& pointSrc,
 HBITMAP hbmMask,
 const POINT& pointMask,
 DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 HBITMAP hbmMask,
 DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
 HDC hDestDC,
 const POINT& pointDest,
 HBITMAP hbmMask,
 DWORD dwROP = SRCCOPY) const throw();
```  
  
### <a name="parameters"></a>參數  
 `hDestDC`  
 其可執行檔包含資源模組控制代碼。  
  
 `xDest`  
 X 軸座標，以邏輯單位目的矩形左上角。  
  
 `yDest`  
 Y 軸座標，以邏輯單位目的矩形左上角。  
  
 `nDestWidth`  
 以邏輯單位，目的地矩形和來源點陣圖的寬度。  
  
 `nDestHeight`  
 以邏輯單位，目的地矩形和來源點陣圖的高度。  
  
 `xSrc`  
 邏輯 x 座標的來源點陣圖左上角。  
  
 `ySrc`  
 邏輯 y 座標的來源點陣圖左上角。  
  
 `hbmMask`  
 結合的來源裝置內容中的色彩點陣圖黑白遮罩點陣圖的控制代碼。  
  
 `xMask`  
 所指定的遮罩點陣圖的水平像素位移`hbmMask`參數。  
  
 `yMask`  
 所指定的遮罩點陣圖的像素垂直位移`hbmMask`參數。  
  
 `dwROP`  
 指定前景和背景三元點陣化操作程式碼的方法用來控制來源和目的地資料的組合。 背景的點陣作業程式碼會儲存在此值; 高序位文字的高序位位元組前景點陣作業程式碼會儲存在此值; 高序位文字的低序位位元組此值的低序位文字會被忽略，而且必須為零。 如需前景和背景，這個方法的內容中的討論，請參閱`MaskBlt`中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 如需常見的點陣作業程式碼，請參閱`BitBlt`中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `rectDest`  
 參考`RECT`結構，用來識別目的地。  
  
 `pointSrc`  
 A`POINT`結構，表示來源矩形左上的角。  
  
 `pointMask`  
 A**點**結構表示遮罩點陣圖左上的角。  
  
 `pointDest`  
 參考**點**識別的邏輯單元的目的矩形左上的角的結構。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 這個方法適用於 Windows NT 4.0 版及更新版本的唯一版本。  
  
##  <a name="operator_hbitmap"></a>CImage::operator HBITMAP  
 使用這個運算子來取得附加的 Windows GDI 控制代碼的`CImage`物件。 這位操作員便轉型運算子，支援直接使用`HBITMAP`物件。  
  
##  <a name="plgblt"></a>Cimage:: Plgblt  
 執行從來源裝置內容中的矩形的位元區塊傳輸，變成平行四邊形在目的地裝置內容中。  
  
```
BOOL PlgBlt(
 HDC hDestDC,
 const POINT* pPoints,
 HBITMAP hbmMask = NULL) const throw();

BOOL PlgBlt(
 HDC hDestDC,
 const POINT* pPoints,
 int xSrc,
 int ySrc,
 int nSrcWidth,
 int nSrcHeight,
 HBITMAP hbmMask = NULL,
 int xMask = 0,
 int yMask = 0) const throw();

BOOL PlgBlt(
 HDC hDestDC,
 const POINT* pPoints,
 const RECT& rectSrc,
 HBITMAP hbmMask = NULL,
 const POINT& pointMask = CPoint(0, 0)) const throw();
```  
  
### <a name="parameters"></a>參數  
 `hDestDC`  
 目的地裝置內容控制代碼。  
  
 *pPoints*  
 邏輯空間中找出三個角目的平行四邊形的三個點的陣列指標。 來源矩形左上的角對應到在這個陣列、 在陣列中，第二點右上角和左下的角的第三個點的第一個點。 來源矩形的右下角會對應至的平行四邊形中隱含的第四個點。  
  
 `hbmMask`  
 用來遮罩來源矩形的色彩選擇性單色點陣圖控制代碼。  
  
 `xSrc`  
 X 座標，以邏輯單位，來源矩形左上角。  
  
 `ySrc`  
 Y 座標，以邏輯單位，來源矩形左上角。  
  
 `nSrcWidth`  
 以邏輯單位，來源矩形的寬度。  
  
 `nSrcHeight`  
 以邏輯單位，來源矩形的高度。  
  
 `xMask`  
 單色點陣圖左上角的 x 座標。  
  
 `yMask`  
 單色點陣圖左上角的 y 座標。  
  
 `rectSrc`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，指定來源矩形的座標。  
  
 `pointMask`  
 A[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)結構表示遮罩點陣圖左上的角。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`hbmMask`識別有效的單色點陣圖， **PlgBit**遮罩從來源矩形的色彩資料位元會使用這個點陣圖。  
  
 這個方法適用於 Windows NT 4.0 版及更新版本的唯一版本。 請參閱[PlgBlt](http://msdn.microsoft.com/library/windows/desktop/dd162804)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]如需詳細資訊。  
  
##  <a name="releasedc"></a>CImage::ReleaseDC  
 釋放裝置內容。  
  
```
void ReleaseDC() const throw();
```  
  
### <a name="remarks"></a>備註  
 因為只有一個點陣圖可以放入裝置內容中選取一次，您必須呼叫`ReleaseDC`每次呼叫[GetDC](#getdc)。  
  
##  <a name="releasegdiplus"></a>CImage::ReleaseGDIPlus  
 GDI + 所使用的資源釋出。  
  
```
void ReleaseGDIPlus() throw();
```  
  
### <a name="remarks"></a>備註  
 必須呼叫這個方法，以釋放資源配置的全域`CImage`物件。 請參閱[CImage::CImage](#cimage)。  
  
##  <a name="save"></a>CImage::Save  
 將影像儲存至指定的資料流或檔案在磁碟上。  
  
```
HRESULT Save(IStream* pStream,
 REFGUID guidFileType) const throw();

HRESULT Save(LPCTSTR pszFileName,
 REFGUID guidFileType= GUID_NULL) const throw();
```  
  
### <a name="parameters"></a>參數  
 `pStream`  
 COM IStream 物件，包含檔案映像資料指標。  
  
 *pszFileName*  
 指標影像的檔案名稱。  
  
 `guidFileType`  
 要儲存映像的檔案類型。 可以是下列其中一項：  
  
- **ImageFormatBMP**的未壓縮的點陣圖影像。  
  
- **ImageFormatPNG**可攜式網路圖形 (PNG) 壓縮映像。  
  
- **ImageFormatJPEG** JPEG 壓縮映像。  
  
- **ImageFormatGIF** GIF 壓縮映像。  
  
> [!NOTE]
>  如需常數的完整清單，請參閱**影像檔案格式常數**中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
### <a name="remarks"></a>備註  
 呼叫此函式可儲存的映像，使用指定的名稱和型別。 如果`guidFileType`不包含參數、 檔案名稱副檔名將用於決定映像格式。 如果提供沒有副檔名，則影像會儲存 BMP 格式。  
  
##  <a name="setcolortable"></a>CImage::SetColorTable  
 DIB 區段的調色盤中設定的紅色、 綠色、 藍色 (RGB) 色彩值的項目範圍。  
  
```
void SetColorTable(
  UINT iFirstColor, 
  UINT nColors,
  const RGBQUAD* prgbColors) throw();
```  
  
### <a name="parameters"></a>參數  
 `iFirstColor`  
 若要設定的第一個項目色彩資料表索引。  
  
 `nColors`  
 若要設定的色彩表項目數。  
  
 `prgbColors`  
 陣列的指標[RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)結構，以設定色彩表項目。  
  
### <a name="remarks"></a>備註  
 這個方法支援 DIB 區段點陣圖。  
  
##  <a name="setpixel"></a>CImage::SetPixel  
 設定在點陣圖中的指定位置的像素色彩。  
  
```
void SetPixel(int x, int y, COLORREF color) throw();
```  
  
### <a name="parameters"></a>參數  
 *x*  
 若要設定的像素水平位置。  
  
 *y*  
 若要設定的像素垂直位置。  
  
 `color`  
 要設定像素的色彩。  
  
### <a name="remarks"></a>備註  
 如果像素座標所選的裁剪區域外的即時，這個方法將會失敗。  
  
##  <a name="setpixelindexed"></a>CImage::SetPixelIndexed  
 設定像素色彩的色彩位於`iIndex`調色盤的色彩。  
  
```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```  
  
### <a name="parameters"></a>參數  
 *x*  
 若要設定的像素水平位置。  
  
 *y*  
 若要設定的像素垂直位置。  
  
 `iIndex`  
 色彩調色盤中的索引。  
  
##  <a name="setpixelrgb"></a>CImage::SetPixelRGB  
 設定所指定位置的像素*x*和*y*所指示的色彩*r*， *g*，和*b*、 以紅色、 綠色、 藍色 (RGB) 映像。  
  
```
void SetPixelRGB(  
 int x,
 int y,
 BYTE r,
 BYTE g,
 BYTE b) throw();
```  
  
### <a name="parameters"></a>參數  
 *x*  
 若要設定的像素水平位置。  
  
 *y*  
 若要設定的像素垂直位置。  
  
 *r*  
 紅色色彩的濃度。  
  
 *g*  
 綠色色彩的濃度。  
  
 *b*  
 藍色色彩的濃度。  
  
### <a name="remarks"></a>備註  
 紅色、 綠色和藍色參數會分別表示一個介於 0 和 255 之間的數字。 如果您將所有三個參數設定為零，則合併結果色彩為黑色。 如果您設定所有三個參數為 255，合併結果色彩為白色。  
  
##  <a name="settransparentcolor"></a>CImage::SetTransparentColor  
 設定在指定索引位置為透明的色彩。  
  
```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```  
  
### <a name="parameters"></a>參數  
 *iTransparentColor*  
 若要設定為透明色彩的調色盤中的索引。 –&1;，如果沒有色彩設為透明。  
  
### <a name="return-value"></a>傳回值  
 先前的色彩索引設定為透明。  
  
##  <a name="stretchblt"></a>CImage::StretchBlt  
 來源裝置內容的點陣圖複製到這個目前的裝置內容。  
  
```
BOOL StretchBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
 HDC hDestDC,
 const RECT& rectDest,
 DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 int xSrc,
 int ySrc,
 int nSrcWidth,
 int nSrcHeight,
 DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
 HDC hDestDC,
 const RECT& rectDest,
 const RECT& rectSrc,
 DWORD dwROP = SRCCOPY) const throw();
```  
  
### <a name="parameters"></a>參數  
 `hDestDC`  
 目的地裝置內容控制代碼。  
  
 `xDest`  
 X 軸座標，以邏輯單位目的矩形左上角。  
  
 `yDest`  
 Y 軸座標，以邏輯單位目的矩形左上角。  
  
 `nDestWidth`  
 以邏輯單位，目的地矩形的寬度。  
  
 `nDestHeight`  
 以邏輯單位，目的地矩形的高度。  
  
 `dwROP`  
 要執行的點陣作業。 點陣作業程式碼會定義如何合併來源、 目的地和模式的位元 （如目前選取的筆刷所定義） 為目的地。 請參閱[BitBlt](http://msdn.microsoft.com/library/windows/desktop/dd183370)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]其他點陣化操作碼及其描述的清單。  
  
 `rectDest`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，用來識別目的地。  
  
 `xSrc`  
 X 座標，以邏輯單位，來源矩形左上角。  
  
 `ySrc`  
 Y 座標，以邏輯單位，來源矩形左上角。  
  
 `nSrcWidth`  
 以邏輯單位，來源矩形的寬度。  
  
 `nSrcHeight`  
 以邏輯單位，來源矩形的高度。  
  
 `rectSrc`  
 參考`RECT`結構，來識別來源。  
  
### <a name="return-value"></a>傳回值  
 非零，如果成功，否則為 0。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[StretchBlt](http://msdn.microsoft.com/library/windows/desktop/dd145120)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="transparentblt"></a>Transparentblt  
 來源裝置內容的點陣圖複製到這個目前的裝置內容。  
  
```
BOOL TransparentBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
 HDC hDestDC,
 const RECT& rectDest,
 UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
 HDC hDestDC,
 int xDest,
 int yDest,
 int nDestWidth,
 int nDestHeight,
 int xSrc,
 int ySrc,
 int nSrcWidth,
 int nSrcHeight,
 UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
 HDC hDestDC,
 const RECT& rectDest,
 const RECT& rectSrc,
 UINT crTransparent = CLR_INVALID) const throw();
```  
  
### <a name="parameters"></a>參數  
 `hDestDC`  
 目的地裝置內容控制代碼。  
  
 `xDest`  
 X 軸座標，以邏輯單位目的矩形左上角。  
  
 `yDest`  
 Y 軸座標，以邏輯單位目的矩形左上角。  
  
 `nDestWidth`  
 以邏輯單位，目的地矩形的寬度。  
  
 `nDestHeight`  
 以邏輯單位，目的地矩形的高度。  
  
 *crTransparent*  
 中要視為透明的來源點陣圖的色彩。 根據預設， **CLR_INVALID**，表示應該使用目前設定為影像的透明色彩的色彩。  
  
 `rectDest`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構，用來識別目的地。  
  
 `xSrc`  
 X 座標，以邏輯單位，來源矩形左上角。  
  
 `ySrc`  
 Y 座標，以邏輯單位，來源矩形左上角。  
  
 `nSrcWidth`  
 以邏輯單位，來源矩形的寬度。  
  
 `nSrcHeight`  
 以邏輯單位，來源矩形的高度。  
  
 `rectSrc`  
 參考`RECT`結構，來識別來源。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果成功，否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 `TransparentBlt`支援的每個像素和每像素 8 位元的 4 個位元的來源點陣圖。 使用[CImage::AlphaBlend](#alphablend)透明度指定 32 位元和每個像素點陣圖。  
  
  
### <a name="example"></a>範例  

```cpp  
// Performs a transparent blit from the source image to the destination 
// image using the images' current transparency settings
BOOL TransparentBlt(CImage* pSrcImage, CImage* pDstImage, 
       int xDest, int yDest, int nDestWidth, int nDestHeight)
{
  HDC hDstDC = NULL;
  BOOL bResult;

  if(pSrcImage == NULL || pDstImage == NULL)
  {
  // Invalid parameter
  return FALSE;
  }

  // Obtain a DC to the destination image
  hDstDC = pDstImage->GetDC();

  // Perform the blit
  bResult = pSrcImage->TransparentBlt(hDstDC, xDest, yDest, nDestWidth, nDestHeight);

  // Release the destination DC
  pDstImage->ReleaseDC();

  return bResult;
}
```

  
## <a name="see-also"></a>另請參閱  
 [MMXSwarm 範例](../../visual-cpp-samples.md)   
 [SimpleImage 範例](../../visual-cpp-samples.md)   
 [與裝置無關點陣圖](http://msdn.microsoft.com/library/windows/desktop/dd183562)   
 [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183494)   
 [ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)
 [與裝置無關點陣圖](http://msdn.microsoft.com/library/windows/desktop/dd183562)   
 [CreateDIBSection](http://msdn.microsoft.com/library/windows/desktop/dd183494)   










