---
title: "CMFCToolBarImages 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarImages
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarImages class
ms.assetid: d4e50518-9ffc-406f-9996-f79e5cd38155
caps.latest.revision: 31
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ff94497108033b17d52b79594fdbe30e8ed7da03
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarimages-class"></a>CMFCToolBarImages 類別
在工具列上的影像。 `CMFCToolBarImages`類別會管理從應用程式資源，或從檔案載入的工具列影像。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCToolBarImages : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCToolBarImages::CMFCToolBarImages](#cmfctoolbarimages)|建構 `CMFCToolBarImages` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarImages::AdaptColors](#adaptcolors)||  
|[CMFCToolBarImages::AddIcon](#addicon)|將圖示加入至工具列影像。|  
|[CMFCToolBarImages::AddImage](#addimage)|將工具列影像的點陣圖。|  
|[CMFCToolBarImages::CleanUp](#cleanup)||  
|[CMFCToolBarImages::Clear](#clear)|釋放這個物件所配置的系統資源。|  
|[CMFCToolBarImages::ConvertTo32Bits](#convertto32bits)|將轉換加上底線 32 bpp 影像的點陣圖。|  
|[CMFCToolBarImages::CopyImageToClipboard](#copyimagetoclipboard)||  
|[CMFCToolBarImages::CopyTo](#copyto)||  
|[CMFCToolBarImages::CreateFromImageList](#createfromimagelist)|初始化從影像清單的工具列影像 ( [CImageList 類別](../../mfc/reference/cimagelist-class.md))。|  
|[CMFCToolBarImages::CreateRegionFromImage](#createregionfromimage)||  
|[CMFCToolBarImages::DeleteImage](#deleteimage)|刪除具有指定的索引，從工具列映像，如果這組工具列影像包含使用者定義的映像的映像。|  
|[CMFCToolBarImages::Draw](#draw)|繪製單一工具列按鈕影像 （按鈕）。|  
|[CMFCToolBarImages::DrawEx](#drawex)||  
|[CMFCToolBarImages::EnableRTL](#enablertl)||  
|[CMFCToolBarImages::EndDrawImage](#enddrawimage)|工具列按鈕影像繪製後釋放系統資源。|  
|[CMFCToolBarImages::ExtractIcon](#extracticon)|傳回具有指定的影像索引，從工具列影像的圖示。|  
|[CMFCToolBarImages::FillDitheredRect](#fillditheredrect)|使用具有工具列的背景色彩的筆刷，填滿的矩形。|  
|[CMFCToolBarImages::GetAlwaysLight](#getalwayslight)||  
|[CMFCToolBarImages::GetBitsPerPixel](#getbitsperpixel)|傳回目前的解析度，加上底線的映像。|  
|[CMFCToolBarImages::GetCount](#getcount)|在工具列上傳回映像的數目。|  
|[CMFCToolBarImages::GetDisabledImageAlpha](#getdisabledimagealpha)|傳回已停用映像所使用的 alpha 色頻值。|  
|[CMFCToolBarImages::GetFadedImageAlpha](#getfadedimagealpha)||  
|[CMFCToolBarImages::GetImageSize](#getimagesize)|擷取儲存在記憶體 （來源大小），工具列影像的大小或繪製在 （目的地大小） 畫面上的工具列影像的大小。|  
|[CMFCToolBarImages::GetImageWell](#getimagewell)|傳回包含所有的工具列影像的點陣圖的控制代碼。|  
|[CMFCToolBarImages::GetImageWellLight](#getimagewelllight)||  
|[CMFCToolBarImages::GetLastImageRect](#getlastimagerect)||  
|[CMFCToolBarImages::GetLightPercentage](#getlightpercentage)||  
|[CMFCToolBarImages::GetMapTo3DColors](#getmapto3dcolors)||  
|[CMFCToolBarImages::GetMask](#getmask)||  
|[CMFCToolBarImages::GetResourceOffset](#getresourceoffset)|映像索引傳回指定的資源識別碼。|  
|[CMFCToolBarImages::GetScale](#getscale)|傳回目前縮放比例的加底線的映像。|  
|[CMFCToolBarImages::GetTransparentColor](#gettransparentcolor)||  
|[CMFCToolBarImages::GrayImages](#grayimages)|Grays 工具列影像，讓他們看起來已停用。|  
|[CMFCToolBarImages::Is32BitTransparencySupported](#is32bittransparencysupported)|判斷作業系統是否支援 32 位元 alpha 混色。|  
|[CMFCToolBarImages::IsPreMultiplyAutoCheck](#ispremultiplyautocheck)||  
|[CMFCToolBarImages::IsRTL](#isrtl)|決定是否啟用從右至左 (RTL) 支援。|  
|[CMFCToolBarImages::IsReadOnly](#isreadonly)|決定工具列影像是否為唯讀。|  
|[CMFCToolBarImages::IsScaled](#isscaled)|會指示是否會調整的加底線的映像。|  
|[CMFCToolBarImages::IsUserImagesList](#isuserimageslist)|判斷工具列影像的這個集合是否包含使用者定義的映像。|  
|[CMFCToolBarImages::IsValid](#isvalid)|判斷工具列影像的這個集合是否包含有效的工具列按鈕影像。|  
|[CMFCToolBarImages::Load](#load)|從系統資源，或從檔案載入的工具列影像。|  
|[CMFCToolBarImages::LoadStr](#loadstr)||  
|[CMFCToolBarImages::MapFromSysColor](#mapfromsyscolor)||  
|[CMFCToolBarImages::MapTo3dColors](#mapto3dcolors)||  
|[CMFCToolBarImages::MapToSysColor](#maptosyscolor)||  
|[CMFCToolBarImages::MapToSysColorAlpha](#maptosyscoloralpha)||  
|[CMFCToolBarImages::Mirror](#mirror)|水平鏡像處理所有的工具列影像。|  
|[CMFCToolBarImages::MirrorBitmap](#mirrorbitmap)|水平鏡像處理點陣圖。|  
|[CMFCToolBarImages::MirrorBitmapVert](#mirrorbitmapvert)||  
|[CMFCToolBarImages::MirrorVert](#mirrorvert)||  
|[CMFCToolBarImages::OnSysColorChange](#onsyscolorchange)||  
|[CMFCToolBarImages::PrepareDrawImage](#preparedrawimage)|配置工具列按鈕影像繪製於指定的大小所需的資源。|  
|[CMFCToolBarImages::Save](#save)|如果工具列影像的這個集合包含使用者定義的映像，請將工具列影像儲存在檔案中。|  
|[CMFCToolBarImages::SetAlwaysLight](#setalwayslight)||  
|[CMFCToolBarImages::SetDisabledImageAlpha](#setdisabledimagealpha)|設定已停用映像所使用的 alpha 色頻值。|  
|[CMFCToolBarImages::SetFadedImageAlpha](#setfadedimagealpha)||  
|[CMFCToolBarImages::SetImageSize](#setimagesize)|設定工具列按鈕影像 （來源大小） 的大小。|  
|[CMFCToolBarImages::SetLightPercentage](#setlightpercentage)||  
|[CMFCToolBarImages::SetMapTo3DColors](#setmapto3dcolors)||  
|[CMFCToolBarImages::SetPreMultiplyAutoCheck](#setpremultiplyautocheck)||  
|[CMFCToolBarImages::SetSingleImage](#setsingleimage)||  
|[CMFCToolBarImages::SetTransparentColor](#settransparentcolor)|設定工具列影像的透明色彩。|  
|[CMFCToolBarImages::SmoothResize](#smoothresize)|順暢地調整大小加上底線的映像。|  
|[CMFCToolBarImages::UpdateImage](#updateimage)|更新使用者定義工具列按鈕影像的點陣圖。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarImages::PreMultiplyAlpha](#premultiplyalpha)||  
  
### <a name="data-members"></a>資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCToolBarImages::m_bDisableTrueColorAlpha](#m_bdisabletruecoloralpha)|`TRUE`如果已停用 truecolor alpha 混色 （32 位元色彩）。|  
  
## <a name="remarks"></a>備註  
 完整的點陣圖，由下工具列影像`CMFCToolbarImages`固定大小的一或多個的小型工具列影像 （按鈕） 所組成。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定`CMFCToolBarImages`使用各種方法的物件`CMFCToolBarImages`類別。 此範例示範如何設定工具列影像的大小、 載入映像，以及設定影像的透明色彩。 此程式碼片段是一部分[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&32;](../../mfc/codesnippet/cpp/cmfctoolbarimages-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo #&33;](../../mfc/codesnippet/cpp/cmfctoolbarimages-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCToolBarImages`   
  
## <a name="requirements"></a>需求  
 **標頭︰** afxtoolbarimages.h  
  
##  <a name="a-nameadaptcolorsa--cmfctoolbarimagesadaptcolors"></a><a name="adaptcolors"></a>CMFCToolBarImages::AdaptColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void AdaptColors(
    COLORREF clrBase,  
    COLORREF clrTone);
```  
  
### <a name="parameters"></a>參數  
 [in] `clrBase`  
 [in] `clrTone`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameaddicona--cmfctoolbarimagesaddicon"></a><a name="addicon"></a>CMFCToolBarImages::AddIcon  
 將圖示加入至工具列映像的清單。  
  
```  
int AddIcon(
    HICON hIcon,  
    BOOL bAlphaBlend=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `hIcon`  
 要加入之圖示的控制代碼。  
  
 [in] `bAlphaBlend`  
 `TRUE`如果這個圖示搭配 alpha 混色。否則`FALSE`。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，已加入的工具列影像的以零起始的索引否則為-1。  
  
##  <a name="a-nameaddimagea--cmfctoolbarimagesaddimage"></a><a name="addimage"></a>CMFCToolBarImages::AddImage  
 將工具列影像的點陣圖。  
  
```  
int AddImage(
    HBITMAP hbmp,  
    BOOL bSetBitPerPixel=FALSE);

int AddImage(
    const CMFCToolBarImages& imageList,  
    int nIndex);
```  
  
### <a name="parameters"></a>參數  
 [in] `hbmp`  
 若要新增點陣圖控制代碼。  
  
 [in] `bSetBitPerPixel`  
 `TRUE`如果`CMFCToolBarImages`物件會使用新的映像; 的色彩深度 （每像素的位元）`FALSE`如果`CMFCToolbarImages`物件會保留目前的色彩深度。  
  
 [in] `imageList`  
 參考`CMFCToolbarImages`物件，其中包含要加入影像。  
  
 [in] `nIndex`  
 在來源中的索引`CMFCToolbarImages`映像來新增的物件。  
  
### <a name="return-value"></a>傳回值  
 工具列的數字的影像`CMFCToolBarImages`成功; 加入新的點陣圖之後，物件會維護作業失敗時的-1。  
  
##  <a name="a-namecleanupa--cmfctoolbarimagescleanup"></a><a name="cleanup"></a>CMFCToolBarImages::CleanUp  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall CleanUp();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecleara--cmfctoolbarimagesclear"></a><a name="clear"></a>CMFCToolBarImages::Clear  
 釋放系統資源， [CMFCToolbarImages](../../mfc/reference/cmfctoolbarimages-class.md)配置的物件。  
  
```  
void Clear();
```  
  
##  <a name="a-namecmfctoolbarimagesa--cmfctoolbarimagescmfctoolbarimages"></a><a name="cmfctoolbarimages"></a>CMFCToolBarImages::CMFCToolBarImages  
 建構 `CMFCToolBarImages` 物件。  
  
```  
CMFCToolBarImages();
```  
  
### <a name="remarks"></a>備註  
 建構`CMFCToolBarImages`物件，初始化其轉譯引擎，然後將映像大小設為其預設值 16 x 15 像素為單位。 使用[CMFCToolBarImages::SetImageSize](#setimagesize)變更映像大小，才能新增映像。  
  
##  <a name="a-namecopyimagetoclipboarda--cmfctoolbarimagescopyimagetoclipboard"></a><a name="copyimagetoclipboard"></a>CMFCToolBarImages::CopyImageToClipboard  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL CopyImageToClipboard(int iImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `iImage`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecopytoa--cmfctoolbarimagescopyto"></a><a name="copyto"></a>CMFCToolBarImages::CopyTo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL CopyTo(CMFCToolBarImages& imageList);
```  
  
### <a name="parameters"></a>參數  
 [in] `imageList`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namecreatefromimagelista--cmfctoolbarimagescreatefromimagelist"></a><a name="createfromimagelist"></a>CMFCToolBarImages::CreateFromImageList  
 初始化的工具列影像[CImageList 類別](../../mfc/reference/cimagelist-class.md)物件。  
  
```  
BOOL CreateFromImageList(const CImageList& imageList);
```  
  
### <a name="parameters"></a>參數  
 [in] `imageList`  
 可用來做為來源的工具列影像的影像清單。  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `TRUE`。  
  
### <a name="remarks"></a>備註  
 使用此函式來快速初始化工具列的影像清單，從外部影像清單。  
  
##  <a name="a-namecreateregionfromimagea--cmfctoolbarimagescreateregionfromimage"></a><a name="createregionfromimage"></a>CMFCToolBarImages::CreateRegionFromImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static HRGN __stdcall CreateRegionFromImage(
    HBITMAP bmp,  
    COLORREF clrTransparent);
```  
  
### <a name="parameters"></a>參數  
 [in] `bmp`  
 [in] `clrTransparent`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namedeleteimagea--cmfctoolbarimagesdeleteimage"></a><a name="deleteimage"></a>CMFCToolBarImages::DeleteImage  
 刪除使用者定義的映像已指定的索引，從工具列影像。  
  
```  
BOOL DeleteImage(int iImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `iImage`  
 指定要刪除映像的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果映像已順利啟動。`FALSE`映像索引是無效的如果`CMFCToolbarImages`物件是暫時性的`CMFCToolbarImages`物件不包含使用者定義的映像，或如果其他錯誤。  
  
##  <a name="a-namedrawa--cmfctoolbarimagesdraw"></a><a name="draw"></a>CMFCToolBarImages::Draw  
 繪製單一工具列按鈕影像。  
  
```  
BOOL Draw(
    CDC* pDC,  
    int x,  
    int y,  
    int iImageIndex,  
    BOOL bHilite=FALSE,  
    BOOL bDisabled=FALSE,  
    BOOL bIndeterminate=FALSE,  
    BOOL bShadow=FALSE,  
    BOOL bInactive=FALSE,  
    BYTE alphaSrc=255);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `x`  
 左側影像要繪製的矩形的 X 座標。  
  
 [in] `y`  
 影像要繪製的矩形頂端的 Y 座標。  
  
 [in] `iImageIndex`  
 顯示影像的以零為起始的索引。  
  
 [in] `bHilite`  
 `TRUE`如果影像會反白顯示。否則`FALSE`。  
  
 [in] `bDisabled`  
 `TRUE`如果影像繪製停用的樣式。否則`FALSE`。  
  
 [in] `bIndeterminate`  
 `TRUE`如果影像繪製不定狀態的樣式。否則`FALSE`。  
  
 [in] `bShadow`  
 `TRUE`如果有陰影; 要繪製的映像否則`FALSE`。  
  
 [in] `bInactive`  
 `TRUE`如果影像繪製非作用中狀態的樣式。否則`FALSE`。  
  
 [in] `alphaSrc`  
 Alpha 色板 (opacity) 值。 值為 255 表示映像會繪製不透明。 值為 0 表示影像繪製透明。 只有 32 位元彩色影像和顯示 Windows Vista 玻璃樣式的映像，則會使用此值。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果指定的影像顯示可順利啟動。`FALSE`如果映像索引不正確或發生其他錯誤。  
  
##  <a name="a-namedrawexa--cmfctoolbarimagesdrawex"></a><a name="drawex"></a>CMFCToolBarImages::DrawEx  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL DrawEx(
    CDC* pDC,  
    CRect rect,  
    int iImageIndex,  
    ImageAlignHorz horzAlign = ImageAlignHorzLeft,  
    ImageAlignVert vertAlign = ImageAlignVertTop,  
    CRect rectSrc = CRect(0,
    0,
    0,
    0),  
    BYTE alphaSrc = 255);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 [in] `rect`  
 [in] `iImageIndex`  
 [in] `horzAlign`  
 [in] `vertAlign`  
 [in] `rectSrc`  
 [in] `0`  
 [in] `0)`  
 [in] `alphaSrc`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameenablertla--cmfctoolbarimagesenablertl"></a><a name="enablertl"></a>CMFCToolBarImages::EnableRTL  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall EnableRTL(BOOL bIsRTL = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bIsRTL`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameenddrawimagea--cmfctoolbarimagesenddrawimage"></a><a name="enddrawimage"></a>CMFCToolBarImages::EndDrawImage  
 釋放系統資源， [CMFCToolBarImages::PrepareDrawImage](#preparedrawimage)配置工具列按鈕影像繪製呼叫之後[CMFCToolBarImages::Draw](#draw)。  
  
```  
void EndDrawImage(CAfxDrawState& ds);
```  
  
### <a name="parameters"></a>參數  
 [in] `ds`  
 參考`CAfxDrawState`物件傳遞給`PrepareDrawImage`方法。  
  
##  <a name="a-nameextracticona--cmfctoolbarimagesextracticon"></a><a name="extracticon"></a>CMFCToolBarImages::ExtractIcon  
 傳回具有指定的影像索引，從工具列影像的圖示。  
  
```  
HICON ExtractIcon(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 [in] `nIndex`  
 要以圖示擷取映像所在的影像清單中以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 擷取圖示的控制代碼或`NULL`如果`nIndex`超出範圍。  
  
##  <a name="a-namefillditheredrecta--cmfctoolbarimagesfillditheredrect"></a><a name="fillditheredrect"></a>CMFCToolBarImages::FillDitheredRect  
 填滿的矩形以工具列的背景色彩。  
  
```  
static void FillDitheredRect(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>參數  
 [in] `pDC`  
 裝置內容的指標。  
  
 [in] `rect`  
 要填滿的矩形座標。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法，使用系統色彩 COLOR_BTNFACE 和 COLOR_BTNHIGHLIGHT 平均色彩填滿的矩形。 如果系統使用較少或 256 色，矩形系統會填入這兩種色彩遞色圖樣。  
  
##  <a name="a-namegetalwayslighta--cmfctoolbarimagesgetalwayslight"></a><a name="getalwayslight"></a>CMFCToolBarImages::GetAlwaysLight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL GetAlwaysLight() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetcounta--cmfctoolbarimagesgetcount"></a><a name="getcount"></a>CMFCToolBarImages::GetCount  
 工具列影像清單中傳回映像的數目。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 中的映像數目`CMFCToolBarImages`物件。  
  
##  <a name="a-namegetdisabledimagealphaa--cmfctoolbarimagesgetdisabledimagealpha"></a><a name="getdisabledimagealpha"></a>CMFCToolBarImages::GetDisabledImageAlpha  
 傳回已停用映像所使用的 alpha 色頻 (opacity) 值。  
  
```  
static BYTE GetDisabledImageAlpha();
```  
  
### <a name="return-value"></a>傳回值  
 目前的 alpha 色頻值。  
  
### <a name="remarks"></a>備註  
 您可以呼叫[CMFCToolBarImages::SetDisabledImageAlpha](#setdisabledimagealpha)正值 alpha 色頻。  
  
##  <a name="a-namegetfadedimagealphaa--cmfctoolbarimagesgetfadedimagealpha"></a><a name="getfadedimagealpha"></a>CMFCToolBarImages::GetFadedImageAlpha  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BYTE __stdcall GetFadedImageAlpha();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetimagesizea--cmfctoolbarimagesgetimagesize"></a><a name="getimagesize"></a>CMFCToolBarImages::GetImageSize  
 擷取儲存在記憶體 （來源大小），工具列影像的大小或繪製在 （目的地大小） 畫面上的工具列影像的大小。  
  
```  
SIZE GetImageSize(BOOL bDest=FALSE) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `bDest`  
 `TRUE`若要擷取的目標大小;`FALSE`擷取來源映像大小。  
  
### <a name="return-value"></a>傳回值  
 A`SIZE`結構，指定影像的大小，單位為像素。  
  
### <a name="remarks"></a>備註  
 來源影像的大小就是儲存在映像的大小[CMFCToolbarImages](../../mfc/reference/cmfctoolbarimages-class.md)物件。 您可以呼叫[CMFCToolBarImages::SetImageSize](#setimagesize)設定來源大小。 預設值為 16 x 15 像素。  
  
 根據預設，目的地映像大小為 0x0。 當您呼叫時，指定目的地大小[CMFCToolBarImages::PrepareDrawImage](#preparedrawimage)。 [CMFCToolBarImages::EndDrawImage](#enddrawimage)方法目的地大小重設為預設值。  
  
##  <a name="a-namegetimagewella--cmfctoolbarimagesgetimagewell"></a><a name="getimagewell"></a>CMFCToolBarImages::GetImageWell  
 傳回包含所有的工具列影像的點陣圖的控制代碼。  
  
```  
HBITMAP GetImageWell() const;  
```  
  
### <a name="return-value"></a>傳回值  
 包含工具列影像的點陣圖控制代碼。  
  
### <a name="remarks"></a>備註  
 工具列影像會儲存在單一點陣圖，也就是一個資料列在*映像以及*。 若要尋找映像格式工具列按鈕影像，乘以影像索引工具列影像的寬度 (請參閱[CMFCToolBarImages::GetImageSize](#getimagesize)) 也取得映像內的影像的水平位移。  
  
##  <a name="a-namegetimagewelllighta--cmfctoolbarimagesgetimagewelllight"></a><a name="getimagewelllight"></a>CMFCToolBarImages::GetImageWellLight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
HBITMAP GetImageWellLight() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetlastimagerecta--cmfctoolbarimagesgetlastimagerect"></a><a name="getlastimagerect"></a>CMFCToolBarImages::GetLastImageRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetLastImageRect() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetlightpercentagea--cmfctoolbarimagesgetlightpercentage"></a><a name="getlightpercentage"></a>CMFCToolBarImages::GetLightPercentage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetLightPercentage() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetmapto3dcolorsa--cmfctoolbarimagesgetmapto3dcolors"></a><a name="getmapto3dcolors"></a>CMFCToolBarImages::GetMapTo3DColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL GetMapTo3DColors() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetmaska--cmfctoolbarimagesgetmask"></a><a name="getmask"></a>CMFCToolBarImages::GetMask  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
HBITMAP GetMask(int iImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `iImage`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetresourceoffseta--cmfctoolbarimagesgetresourceoffset"></a><a name="getresourceoffset"></a>CMFCToolBarImages::GetResourceOffset  
 映像索引傳回指定的資源識別碼。  
  
```  
int GetResourceOffset(UINT uiResId) const;  
```  
  
### <a name="parameters"></a>參數  
 [in] `uiResId`  
 影像資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 映像索引，如果方法成功。為-1 的映像與指定的資源識別碼不存在。  
  
##  <a name="a-namegettransparentcolora--cmfctoolbarimagesgettransparentcolor"></a><a name="gettransparentcolor"></a>CMFCToolBarImages::GetTransparentColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
COLORREF GetTransparentColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegrayimagesa--cmfctoolbarimagesgrayimages"></a><a name="grayimages"></a>CMFCToolBarImages::GrayImages  
 Grays 工具列影像，讓他們看起來已停用。  
  
```  
BOOL GrayImages(int nGrayImageLuminancePercentage);
```  
  
### <a name="parameters"></a>參數  
 [in] `nGrayImageLuminancePercentage`  
 亮度百分比。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果集合中的映像變成灰色順利啟動。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法會修改工具列影像的平均每個像素的紅色、 綠色和藍色元件和相乘的結果`nGrayImageLuminancePercentage`除以 100。 如果`nGrayImageLuminancePercentage`為零或負值，130 的預設值改用。  
  
> [!NOTE]
>  如果您想復原變更，您必須重新載入從來源映像。 您可以藉由呼叫[CMFCToolBarImages::Load](#load)或[CMFCToolBarImages::UpdateImage](#updateimage) （僅適用於使用者定義的映像），或藉由呼叫[CMFCToolBarImages::Clear](#clear)以及一次新增映像，藉由呼叫[CMFCToolBarImages::AddIcon](#addicon)或[CMFCToolBarImages::AddImage](#addimage)。  
  
##  <a name="a-nameis32bittransparencysupporteda--cmfctoolbarimagesis32bittransparencysupported"></a><a name="is32bittransparencysupported"></a>CMFCToolBarImages::Is32BitTransparencySupported  
 指定作業系統是否支援 32 位元 alpha 混色。  
  
```  
static BOOL Is32BitTransparencySupported();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果可支援 32 位元 alpha 混色。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 使用這個靜態方法，在執行階段判斷作業系統是否支援 32 位元 alpha 混色。 支援這項功能[!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)]和更新版本。  
  
##  <a name="a-nameispremultiplyautochecka--cmfctoolbarimagesispremultiplyautocheck"></a><a name="ispremultiplyautocheck"></a>CMFCToolBarImages::IsPreMultiplyAutoCheck  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsPreMultiplyAutoCheck() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisreadonlya--cmfctoolbarimagesisreadonly"></a><a name="isreadonly"></a>CMFCToolBarImages::IsReadOnly  
 指定工具列影像是否為唯讀。  
  
```  
BOOL IsReadOnly() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果工具列影像是唯讀的否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 `CMFCToolbarImages`物件是唯讀或複製中使用的點陣圖時從唯讀的檔案，載入的工具列影像的點陣圖`CMFCToolBarImages::CopyTemp`方法。  
  
##  <a name="a-nameisrtla--cmfctoolbarimagesisrtl"></a><a name="isrtl"></a>CMFCToolBarImages::IsRTL  
 指定是否啟用從右至左 (RTL) 支援。  
  
```  
static BOOL IsRTL();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已啟用從右至左支援;否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 當應用程式會讀取由右至左，阿拉伯文、 希伯來文、 波斯文、 或烏都文等語言進行當地語系化，則會使用從右至左支援。  
  
##  <a name="a-nameisuserimageslista--cmfctoolbarimagesisuserimageslist"></a><a name="isuserimageslist"></a>CMFCToolBarImages::IsUserImagesList  
 指定的工具列影像的這個集合是否包含使用者定義的映像。  
  
```  
BOOL IsUserImagesList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`CMFCToolBarImages`物件包含使用者定義的工具列影像，否則為`FALSE`。  
  
##  <a name="a-nameisvalida--cmfctoolbarimagesisvalid"></a><a name="isvalid"></a>CMFCToolBarImages::IsValid  
 指出這個工具列影像的集合是否包含有效的工具列按鈕影像。  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果`CMFCToolBarImages`物件是有效的否則為`FALSE`。  
  
### <a name="remarks"></a>備註  
 `CMFCToolBarImages`時物件不是有效的工具列影像的點陣圖控制代碼是`NULL`。  
  
##  <a name="a-nameloada--cmfctoolbarimagesload"></a><a name="load"></a>CMFCToolBarImages::Load  
 從系統資源，或從檔案載入的工具列影像。  
  
```  
BOOL Load(
    UINT uiResID,  
    HINSTANCE hinstRes=NULL,  
    BOOL bAdd=FALSE);

BOOL Load(
    LPCTSTR lpszBmpFileName,   
    DWORD nMaxFileSize = 819200);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiResID`  
 點陣圖資源的識別碼。  
  
 [in] `hinstRes`  
 資源 DLL 的執行個體。  
  
 [in] `bAdd`  
 `TRUE`加入現有的點陣圖，載入的點陣圖或`FALSE`來取代現有的點陣圖。  
  
 [in] `lpszBmpFileName`  
 要從中載入點陣圖磁碟檔案的路徑。  
  
 [in] `nMaxFileSize`  
 點陣圖檔案中的位元組數目上限或 0 表示載入點陣圖，不論檔案大小。 如果檔案大小超過此大小上限，則方法會傳回`FALSE`並不會載入點陣圖。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 載入點陣圖否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 如果檔案具有唯讀屬性，影像清單被標示為唯讀。  
  
##  <a name="a-nameloadstra--cmfctoolbarimagesloadstr"></a><a name="loadstr"></a>CMFCToolBarImages::LoadStr  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL LoadStr(
    LPCTSTR lpszResourceName,  
    HINSTANCE hinstRes = NULL,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpszResourceName`  
 [in] `hinstRes`  
 [in] `bAdd`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemapfromsyscolora--cmfctoolbarimagesmapfromsyscolor"></a><a name="mapfromsyscolor"></a>CMFCToolBarImages::MapFromSysColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static COLORREF __stdcall MapFromSysColor(
    COLORREF color,  
    BOOL bUseRGBQUAD = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `color`  
 [in] `bUseRGBQUAD`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemapto3dcolorsa--cmfctoolbarimagesmapto3dcolors"></a><a name="mapto3dcolors"></a>CMFCToolBarImages::MapTo3dColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL MapTo3dColors(
    BOOL bUseRGBQUAD = TRUE,  
    COLORREF clrSrc = (COLORREF)-1,  
    COLORREF clrDest = (COLORREF)-1);
```  
  
### <a name="parameters"></a>參數  
 [in] `bUseRGBQUAD`  
 [in] `clrSrc`  
 [in] `clrDest`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemaptosyscolora--cmfctoolbarimagesmaptosyscolor"></a><a name="maptosyscolor"></a>CMFCToolBarImages::MapToSysColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static COLORREF __stdcall MapToSysColor(
    COLORREF color,  
    BOOL bUseRGBQUAD = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `color`  
 [in] `bUseRGBQUAD`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemaptosyscoloralphaa--cmfctoolbarimagesmaptosyscoloralpha"></a><a name="maptosyscoloralpha"></a>CMFCToolBarImages::MapToSysColorAlpha  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static COLORREF __stdcall MapToSysColorAlpha(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 [in] `color`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemirrora--cmfctoolbarimagesmirror"></a><a name="mirror"></a>CMFCToolBarImages::Mirror  
 取代其水平的鏡映影像的工具列影像。  
  
```  
BOOL Mirror();
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功鏡像映像。，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 這個方法用來支援由右至左書寫系統。  
  
##  <a name="a-namemirrorbitmapa--cmfctoolbarimagesmirrorbitmap"></a><a name="mirrorbitmap"></a>CMFCToolBarImages::MirrorBitmap  
 點陣圖，取代其水平的鏡映影像。  
  
```  
static BOOL MirrorBitmap(
    HBITMAP& hbmp,  
    int cxImage);
```  
  
### <a name="parameters"></a>參數  
 [in、out] `hbmp`  
 鏡像點陣圖控制代碼。  
  
 [in] `cxImage`  
 單位為像素影像的寬度。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功鏡像映像。，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 此函式用來支援由右至左書寫系統。  
  
##  <a name="a-namemirrorbitmapverta--cmfctoolbarimagesmirrorbitmapvert"></a><a name="mirrorbitmapvert"></a>CMFCToolBarImages::MirrorBitmapVert  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BOOL __stdcall MirrorBitmapVert(
    HBITMAP& hbmp,  
    int cyImage);
```  
  
### <a name="parameters"></a>參數  
 [in] `hbmp`  
 [in] `cyImage`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namemirrorverta--cmfctoolbarimagesmirrorvert"></a><a name="mirrorvert"></a>CMFCToolBarImages::MirrorVert  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL MirrorVert();
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameonsyscolorchangea--cmfctoolbarimagesonsyscolorchange"></a><a name="onsyscolorchange"></a>CMFCToolBarImages::OnSysColorChange  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void OnSysColorChange();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namepremultiplyalphaa--cmfctoolbarimagespremultiplyalpha"></a><a name="premultiplyalpha"></a>CMFCToolBarImages::PreMultiplyAlpha  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BOOL __stdcall PreMultiplyAlpha(
    HBITMAP hbmp,  
    BOOL bAutoCheckPremlt);

BOOL PreMultiplyAlpha(HBITMAP hbmp);
```  
  
### <a name="parameters"></a>參數  
 [in] `hbmp`  
 [in] `bAutoCheckPremlt`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namembdisabletruecoloralphaa--cmfctoolbarimagesmbdisabletruecoloralpha"></a><a name="m_bdisabletruecoloralpha"></a>CMFCToolBarImages::m_bDisableTrueColorAlpha  
 `TRUE`如果已停用 truecolor alpha 混色 （32 位元色彩）。  
  
```  
static BOOL m_bDisableTrueColorAlpha;  
```  
  
### <a name="remarks"></a>備註  
 這個成員變數設定為`FALSE`啟用 truecolor 工具列影像 alpha 混色。  
  
 預設值是`TRUE`回溯相容性。  
  
##  <a name="a-namepreparedrawimagea--cmfctoolbarimagespreparedrawimage"></a><a name="preparedrawimage"></a>CMFCToolBarImages::PrepareDrawImage  
 配置工具列按鈕影像繪製於指定的大小所需的資源。  
  
```  
BOOL PrepareDrawImage(
    CAfxDrawState& ds,  
    CSize sizeImageDest=CSize(0,
    0)  
    BOOL bFadeInactive=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `ds`  
 參考`CAfxDrawState`結構，其中儲存影像轉譯階段之間配置的資源。  
  
 [in] `sizeImageDest`  
 指定目的地映像的大小。  
  
 [in] `bFadeInactive`  
 `TRUE`如果您想要非作用中影像繪製漸層。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`若要繪製工具列映像所需的資源配置成功，否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法之後，您可以呼叫[CMFCToolBarImages::Draw](#draw)次數不限。 完成繪圖之後，您必須呼叫[CMFCToolBarImages::EndDrawImage](#enddrawimage)釋放所配置的資源`PrepareDrawImage`。  
  
##  <a name="a-namesavea--cmfctoolbarimagessave"></a><a name="save"></a>CMFCToolBarImages::Save  
 如果工具列影像的這個集合包含使用者定義的映像，請將工具列影像儲存在檔案中。  
  
```  
BOOL Save(LPCTSTR lpszBmpFileName=NULL);
```  
  
### <a name="parameters"></a>參數  
 `lpszBmpFileName`  
 磁碟檔案路徑。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果已成功; 儲存工具列影像否則`FALSE`。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法，將使用者定義的映像儲存至磁碟檔案。 如果`lpszBmpFileName`是`NULL`，方法會將點陣圖儲存至從中載入點陣圖檔[CMFCToolBarImages::Load](#load)方法。  
  
##  <a name="a-namesetalwayslighta--cmfctoolbarimagessetalwayslight"></a><a name="setalwayslight"></a>CMFCToolBarImages::SetAlwaysLight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetAlwaysLight(BOOL bAlwaysLight = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bAlwaysLight`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetdisabledimagealphaa--cmfctoolbarimagessetdisabledimagealpha"></a><a name="setdisabledimagealpha"></a>CMFCToolBarImages::SetDisabledImageAlpha  
 設定已停用映像所使用的 alpha 色頻 (opacity) 值。  
  
```  
static void SetDisabledImageAlpha(BYTE nValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `nValue`  
 Alpha 色頻的新值。  
  
### <a name="remarks"></a>備註  
 使用此方法設定自訂的 alpha 值，已停用映像。 預設值是 127 個，這會導致是半透明的已停用的按鈕影像。 如果您設定的值為 0，已停用映像將會完全透明。 如果您設定的值為 255，停用映像會完全不透明。  
  
##  <a name="a-namesetfadedimagealphaa--cmfctoolbarimagessetfadedimagealpha"></a><a name="setfadedimagealpha"></a>CMFCToolBarImages::SetFadedImageAlpha  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall SetFadedImageAlpha(BYTE nValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `nValue`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetimagesizea--cmfctoolbarimagessetimagesize"></a><a name="setimagesize"></a>CMFCToolBarImages::SetImageSize  
 設定每個工具列按鈕影像 （來源大小） 的大小。  
  
```  
void SetImageSize(
    SIZE sizeImage,  
    BOOL bUpdateCount=FALSE);
```  
  
### <a name="parameters"></a>參數  
 [in] `sizeImage`  
 新的工具列影像的大小。  
  
### <a name="remarks"></a>備註  
 根據預設工具列影像的大小是 16 x 15 像素為單位。 如果您想要使用不同大小的工具列影像，請呼叫這個方法。  
  
##  <a name="a-namesetlightpercentagea--cmfctoolbarimagessetlightpercentage"></a><a name="setlightpercentage"></a>CMFCToolBarImages::SetLightPercentage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetLightPercentage(int nValue);
```  
  
### <a name="parameters"></a>參數  
 [in] `nValue`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetmapto3dcolorsa--cmfctoolbarimagessetmapto3dcolors"></a><a name="setmapto3dcolors"></a>CMFCToolBarImages::SetMapTo3DColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetMapTo3DColors(BOOL bMapTo3DColors);
```  
  
### <a name="parameters"></a>參數  
 [in] `bMapTo3DColors`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetpremultiplyautochecka--cmfctoolbarimagessetpremultiplyautocheck"></a><a name="setpremultiplyautocheck"></a>CMFCToolBarImages::SetPreMultiplyAutoCheck  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetPreMultiplyAutoCheck(BOOL bAuto = TRUE);
```  
  
### <a name="parameters"></a>參數  
 [in] `bAuto`  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesetsingleimagea--cmfctoolbarimagessetsingleimage"></a><a name="setsingleimage"></a>CMFCToolBarImages::SetSingleImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetSingleImage();
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesettransparentcolora--cmfctoolbarimagessettransparentcolor"></a><a name="settransparentcolor"></a>CMFCToolBarImages::SetTransparentColor  
 設定工具列影像的透明色彩。  
  
```  
COLORREF SetTransparentColor(COLORREF clrTransparent);
```  
  
### <a name="parameters"></a>參數  
 [in] `clrTransparent`  
 RGB 值。  
  
### <a name="return-value"></a>傳回值  
 先前的透明色彩。  
  
### <a name="remarks"></a>備註  
 當您或架構呼叫[CMFCToolBarImages::Draw](#draw)，此方法不會描繪符合所指定的色彩的像素`clrTransparent`。  
  
##  <a name="a-nameupdateimagea--cmfctoolbarimagesupdateimage"></a><a name="updateimage"></a>CMFCToolBarImages::UpdateImage  
 更新使用者定義工具列按鈕影像的點陣圖。  
  
```  
BOOL UpdateImage(
    int iImage,  
    HBITMAP hbmp);
```  
  
### <a name="parameters"></a>參數  
 [in] `iImage`  
 若要更新的映像以零為起始的索引。  
  
 [in] `hbmp`  
 點陣圖控制代碼的更新映像。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果映像已順利啟動。`FALSE`如果影像清單不是使用者定義或暫存。  
  
##  <a name="a-nameconvertto32bitsa--cmfctoolbarimagesconvertto32bits"></a><a name="convertto32bits"></a>CMFCToolBarImages::ConvertTo32Bits  
 將轉換加上底線 32 bpp 影像的點陣圖。  
  
```  
BOOL ConvertTo32Bits(COLORREF clrTransparent = (COLORREF)-1);
```  
  
### <a name="parameters"></a>參數  
 `clrTransparent`  
 指定透明色彩的加底線的點陣圖。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetbitsperpixela--cmfctoolbarimagesgetbitsperpixel"></a><a name="getbitsperpixel"></a>CMFCToolBarImages::GetBitsPerPixel  
 傳回目前的解析度，加上底線的映像。  
  
```  
int GetBitsPerPixel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 整數值，表示目前的解析度的加底線的映像，以位元 / 像素 (bpp)。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namegetscalea--cmfctoolbarimagesgetscale"></a><a name="getscale"></a>CMFCToolBarImages::GetScale  
 傳回目前的小數位數比加底線的映像。  
  
```  
double GetScale() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，表示目前的縮放比例。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-nameisscaleda--cmfctoolbarimagesisscaled"></a><a name="isscaled"></a>CMFCToolBarImages::IsScaled  
 會指示是否會調整的加底線的映像。  
  
```  
BOOL IsScaled () const;  
```  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果加上底線的影像會調整。否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="a-namesmoothresizea--cmfctoolbarimagessmoothresize"></a><a name="smoothresize"></a>CMFCToolBarImages::SmoothResize  
 順暢地調整大小加上底線的映像。  
  
```  
BOOL SmoothResize(double dblImageScale);
```  
  
### <a name="parameters"></a>參數  
 `dblImageScale`  
 縮放比例。  
  
### <a name="return-value"></a>傳回值  
 `TRUE`如果成功調整大小;否則`FALSE`。  
  
### <a name="remarks"></a>備註  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarButton 類別](../../mfc/reference/cmfctoolbarbutton-class.md)

