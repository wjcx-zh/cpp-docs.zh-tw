---
title: "CImageList 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CImageList
- AFXCMN/CImageList
- AFXCMN/CImageList::CImageList
- AFXCMN/CImageList::Add
- AFXCMN/CImageList::Attach
- AFXCMN/CImageList::BeginDrag
- AFXCMN/CImageList::Copy
- AFXCMN/CImageList::Create
- AFXCMN/CImageList::DeleteImageList
- AFXCMN/CImageList::DeleteTempMap
- AFXCMN/CImageList::Detach
- AFXCMN/CImageList::DragEnter
- AFXCMN/CImageList::DragLeave
- AFXCMN/CImageList::DragMove
- AFXCMN/CImageList::DragShowNolock
- AFXCMN/CImageList::Draw
- AFXCMN/CImageList::DrawEx
- AFXCMN/CImageList::DrawIndirect
- AFXCMN/CImageList::EndDrag
- AFXCMN/CImageList::ExtractIcon
- AFXCMN/CImageList::FromHandle
- AFXCMN/CImageList::FromHandlePermanent
- AFXCMN/CImageList::GetBkColor
- AFXCMN/CImageList::GetDragImage
- AFXCMN/CImageList::GetImageCount
- AFXCMN/CImageList::GetImageInfo
- AFXCMN/CImageList::GetSafeHandle
- AFXCMN/CImageList::Read
- AFXCMN/CImageList::Remove
- AFXCMN/CImageList::Replace
- AFXCMN/CImageList::SetBkColor
- AFXCMN/CImageList::SetDragCursorImage
- AFXCMN/CImageList::SetImageCount
- AFXCMN/CImageList::SetOverlayImage
- AFXCMN/CImageList::Write
- AFXCMN/CImageList::m_hImageList
dev_langs: C++
helpviewer_keywords:
- CImageList [MFC], CImageList
- CImageList [MFC], Add
- CImageList [MFC], Attach
- CImageList [MFC], BeginDrag
- CImageList [MFC], Copy
- CImageList [MFC], Create
- CImageList [MFC], DeleteImageList
- CImageList [MFC], DeleteTempMap
- CImageList [MFC], Detach
- CImageList [MFC], DragEnter
- CImageList [MFC], DragLeave
- CImageList [MFC], DragMove
- CImageList [MFC], DragShowNolock
- CImageList [MFC], Draw
- CImageList [MFC], DrawEx
- CImageList [MFC], DrawIndirect
- CImageList [MFC], EndDrag
- CImageList [MFC], ExtractIcon
- CImageList [MFC], FromHandle
- CImageList [MFC], FromHandlePermanent
- CImageList [MFC], GetBkColor
- CImageList [MFC], GetDragImage
- CImageList [MFC], GetImageCount
- CImageList [MFC], GetImageInfo
- CImageList [MFC], GetSafeHandle
- CImageList [MFC], Read
- CImageList [MFC], Remove
- CImageList [MFC], Replace
- CImageList [MFC], SetBkColor
- CImageList [MFC], SetDragCursorImage
- CImageList [MFC], SetImageCount
- CImageList [MFC], SetOverlayImage
- CImageList [MFC], Write
- CImageList [MFC], m_hImageList
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1dae44f60c61222659304bea4ee811999d50280b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cimagelist-class"></a>CImageList 類別
提供 Windows 通用影像清單控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CImageList : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CImageList::CImageList](#cimagelist)|建構 `CImageList` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CImageList::Add](#add)|將影像清單的映像或映像。|  
|[CImageList::Attach](#attach)|附加影像清單至`CImageList`物件。|  
|[CImageList::BeginDrag](#begindrag)|開始拖曳影像。|  
|[CImageList::Copy](#copy)|將映像內複製`CImageList`物件。|  
|[CImageList::Create](#create)|初始化影像清單，並將它附加至`CImageList`物件。|  
|[CImageList::DeleteImageList](#deleteimagelist)|刪除映像清單。|  
|[CImageList::DeleteTempMap](#deletetempmap)|由呼叫[CWinApp](../../mfc/reference/cwinapp-class.md)閒置時間處理常式，以刪除任何暫存`CImageList`所建立的物件`FromHandle`。|  
|[CImageList::Detach](#detach)|從影像清單物件卸離`CImageList`物件，並將控制代碼傳回至映像清單。|  
|[CImageList::DragEnter](#dragenter)|在拖曳作業期間鎖定更新，並顯示拖曳影像的指定位置。|  
|[CImageList::DragLeave](#dragleave)|解除鎖定的視窗，並隱藏拖曳影像，以便可以更新視窗。|  
|[CImageList::DragMove](#dragmove)|移動拖放作業期間被拖曳的影像。|  
|[CImageList::DragShowNolock](#dragshownolock)|顯示或隱藏在拖曳作業時，拖曳影像，而無需鎖定的視窗。|  
|[Cimagelist:: Draw](#draw)|繪製拖放作業期間被拖曳的影像。|  
|[CImageList::DrawEx](#drawex)|指定的裝置內容中繪製的映像清單項目。 函式會使用指定的繪製樣式，並混合的映像，以指定的色彩。|  
|[CImageList::DrawIndirect](#drawindirect)|繪製影像的影像清單中。|  
|[CImageList::EndDrag](#enddrag)|結束拖曳作業。|  
|[CImageList::ExtractIcon](#extracticon)|建立為基礎的影像和遮罩影像清單中的圖示。|  
|[CImageList::FromHandle](#fromhandle)|將指標傳回至`CImageList`物件時提供影像清單控制代碼。 如果 `CImageList` 物件沒有附加至控制代碼，會建立並附加暫存 `CImageList` 物件。|  
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|將指標傳回至`CImageList`物件時提供影像清單控制代碼。 如果`CImageList`物件沒有附加至控制代碼， **NULL**傳回。|  
|[CImageList::GetBkColor](#getbkcolor)|擷取目前的背景色彩，影像清單。|  
|[CImageList::GetDragImage](#getdragimage)|取得用於拖曳暫存影像清單。|  
|[CImageList::GetImageCount](#getimagecount)|擷取影像清單中的影像的數目。|  
|[CImageList::GetImageInfo](#getimageinfo)|擷取映像的相關資訊。|  
|[CImageList::GetSafeHandle](#getsafehandle)|擷取**m_hImageList**。|  
|[CImageList::Read](#read)|從封存讀取影像清單。|  
|[CImageList::Remove](#remove)|從影像清單中移除映像。|  
|[CImageList::Replace](#replace)|利用新影像取代影像清單中的映像。|  
|[CImageList::SetBkColor](#setbkcolor)|設定影像清單的背景色彩。|  
|[CImageList::SetDragCursorImage](#setdragcursorimage)|建立新的拖曳影像。|  
|[CImageList::SetImageCount](#setimagecount)|重設影像清單中的映像的計數。|  
|[Cimagelist:: Setoverlayimage](#setoverlayimage)|用於覆疊遮罩的影像清單中加入影像之以零為起始的索引。|  
|[CImageList::Write](#write)|寫入封存中的影像清單。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[CImageList::operator HIMAGELIST](#operator_himagelist)|傳回`HIMAGELIST`附加至`CImageList`。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CImageList::m_hImageList](#m_himagelist)|包含附加至這個物件的影像清單控制代碼。|  
  
## <a name="remarks"></a>備註  
 「 映像清單 」 是相同大小的影像，其中每一個都可以參考其以零為起始的索引集合。 影像清單用來有效管理大量圖示或點陣圖。 影像清單中的所有映像會包含在單一的寬點陣圖螢幕裝置格式。 影像清單也可以包括一個包含遮罩 (用來以透明方式繪製影像) 的單色點陣圖 (圖示樣式)。 Microsoft Win32 應用程式發展介面 (API) 提供可讓您繪製影像、 建立和終結影像清單、 新增和移除影像、 取代影像、 合併影像和拖曳影像的影像清單函式。  
  
 這個控制項 (因此`CImageList`類別) 僅適用於 Windows 95/98、 Windows NT 的版本 3.51 下執行的程式和更新版本。  
  
 如需有關使用`CImageList`，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CImageList](../../mfc/using-cimagelist.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CImageList`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="add"></a>CImageList::Add  
 呼叫此函式可將一或多個影像或圖示新增至映像清單。  
  
```  
int Add(
    CBitmap* pbmImage,  
    CBitmap* pbmMask);

 
int Add(
    CBitmap* pbmImage,  
    COLORREF crMask);  
  
int Add(HICON hIcon);
```  
  
### <a name="parameters"></a>參數  
 `pbmImage`  
 指標，包含影像的點陣圖。 映像數目會推斷從點陣圖的寬度。  
  
 `pbmMask`  
 包含遮罩點陣圖的指標。 如果沒有遮罩影像清單搭配使用，則會忽略這個參數。  
  
 `crMask`  
 用於產生遮罩的色彩。 此指定點陣圖中色彩的每個像素會變更為黑色，且對應的位元遮罩設為一。  
  
 `hIcon`  
 點陣圖和新的映像的遮罩包含圖示的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 以零為起始的第一個新的映像成功; 如果索引否則為-1。  
  
### <a name="remarks"></a>備註  
 您必須負責釋放圖示的控制代碼，當您在使用它。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]  
  
##  <a name="attach"></a>CImageList::Attach  
 呼叫此函式可附加至影像清單`CImageList`物件。  
  
```  
BOOL Attach(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>參數  
 `hImageList`  
 影像清單物件控制代碼。  
  
### <a name="return-value"></a>傳回值  
 附件已成功; 如果為非零否則便是 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]  
  
##  <a name="begindrag"></a>CImageList::BeginDrag  
 呼叫此函式可開始拖曳影像。  
  
```  
BOOL BeginDrag(
    int nImage,  
    CPoint ptHotSpot);
```  
  
### <a name="parameters"></a>參數  
 `nImage`  
 要拖曳的影像以零為起始的索引。  
  
 `ptHotSpot`  
 開始拖放到位置 （通常，資料指標位置） 的座標。 座標是相對於映像的左上角。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式建立暫存影像清單，其中用於拖曳。 映像結合指定的映像和其遮罩與目前的資料指標。 在後續回應`WM_MOUSEMOVE`訊息，您可以利用移動拖曳影像`DragMove`成員函式。 若要結束拖曳作業，您可以使用`EndDrag`成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]  
  
##  <a name="cimagelist"></a>CImageList::CImageList  
 建構 `CImageList` 物件。  
  
```  
CImageList();
```  
  
##  <a name="copy"></a>CImageList::Copy  
 此成員函式實作的 Win32 函式的行為[ImageList_Copy](http://msdn.microsoft.com/library/windows/desktop/bb761520)、 Windows SDK 中所述。  
  
```  
BOOL Copy(
    int iDst,  
    int iSrc,  
    UINT uFlags = ILCF_MOVE);

 
BOOL Copy(
    int iDst,  
    CImageList* pSrc,  
    int iSrc,  
    UINT uFlags = ILCF_MOVE);
```  
  
### <a name="parameters"></a>參數  
 *iDst*  
 使用做為複製作業的目的地之影像的以零為起始的索引。  
  
 `iSrc`  
 要做為複製作業的來源映像的以零為起始的索引。  
  
 `uFlags`  
 位元旗標值，指定要進行複製作業的類型。 這個參數可以是下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|`ILCF_MOVE`|來源映像會複製到目的地映像的索引。 此作業會產生指定之影像的多個執行個體。 `ILCF_MOVE` 是預設值。|  
|`ILCF_SWAP`|來源和目的地影像交換內的影像清單的位置。|  
  
 `pSrc`  
 指標`CImageList`的複製作業目標的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]  
  
##  <a name="create"></a>CImageList::Create  
 初始化影像清單，並將它附加至[CImageList](../../mfc/reference/cimagelist-class.md)物件。  
  
```  
BOOL Create(
    int cx,  
    int cy,  
    UINT nFlags,  
    int nInitial,  
    int nGrow);

 
BOOL Create(
    UINT nBitmapID,  
    int cx,  
    int nGrow,  
    COLORREF crMask);

 
BOOL Create(
    LPCTSTR lpszBitmapID,  
    int cx,  
    int nGrow,  
    COLORREF crMask);

 
BOOL Create(
    CImageList& imagelist1,  
    int nImage1,  
    CImageList& imagelist2,  
    int nImage2,  
    int dx,  
    int dy);  
  
BOOL Create(CImageList* pImageList);
```  
  
### <a name="parameters"></a>參數  
 `cx`  
 單位為像素的每個影像的維度。  
  
 `cy`  
 單位為像素的每個影像的維度。  
  
 `nFlags`  
 指定要建立影像清單的類型。 這個參數可以是下列值的組合，但是它可以包含的其中之一`ILC_COLOR`值。  
  
|值|意義|  
|-----------|-------------|  
|`ILC_COLOR`|使用預設行為，如果沒有其他`ILC_COLOR`* 指定旗標。 一般而言，預設值是`ILC_COLOR4`; 但較舊的顯示驅動程式的預設值是`ILC_COLORDDB`。|  
|`ILC_COLOR4`|使用稱為點陣圖的 4 位元 （16 色） 裝置獨立點陣圖 (DIB) 區段的影像清單。|  
|`ILC_COLOR8`|使用 8 位元 DIB > 一節。 色彩資料表所使用的色彩為相同的半色調調色盤的色彩。|  
|`ILC_COLOR16`|使用 16 位元 (32/64 k 色彩) DIB > 一節。|  
|`ILC_COLOR24`|使用 24 位元 DIB 區段。|  
|`ILC_COLOR32`|使用 32 位元 DIB 區段。|  
|`ILC_COLORDDB`|使用裝置而異的點陣圖。|  
|`ILC_MASK`|使用遮罩。 影像清單包含兩個點陣圖，其中是當做遮罩的單色點陣圖。 如果不包含此值，則影像清單包含只有一個點陣圖。 請參閱[從影像清單的繪圖影像](../../mfc/drawing-images-from-an-image-list.md)遮罩影像上的其他資訊。|  
  
 `nInitial`  
 一開始包含影像清單的映像數目。  
  
 `nGrow`  
 依據系統需要調整大小以讓出空間給新的映像清單時所能成長的影像清單的映像數目。 這個參數代表調整大小的影像清單可包含的新映像的數目。  
  
 `nBitmapID`  
 資源識別碼點陣圖的影像清單與相關聯。  
  
 `crMask`  
 用於產生遮罩的色彩。 此指定點陣圖中色彩的每個像素變更為黑色，和對應的位元遮罩設為一。  
  
 `lpszBitmapID`  
 字串，包含資源的映像的識別碼。  
  
 `imagelist1`  
 對 `CImageList` 物件的參考。  
  
 `nImage1`  
 第一個現有的映像的索引。  
  
 `imagelist2`  
 對 `CImageList` 物件的參考。  
  
 `nImage2`  
 第二個現有映像的索引。  
  
 `dx`  
 中的第一個影像，單位為像素的關聯性的第二個影像的 x 軸的位移。  
  
 `dy`  
 第二個映像的關聯性的第一個影像，單位為像素的 y 軸的位移。  
  
 `pImageList`  
 指標`CImageList`物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CImageList`分成兩個步驟。 首先，呼叫建構函式，然後呼叫`Create`，建立映像清單，並將它附加至`CImageList`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]  
  
##  <a name="deleteimagelist"></a>CImageList::DeleteImageList  
 呼叫此函式來刪除影像清單。  
  
```  
BOOL DeleteImageList();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]  
  
##  <a name="deletetempmap"></a>CImageList::DeleteTempMap  
 會自動呼叫`CWinApp`閒置時間處理常式，`DeleteTempMap`刪除任何暫存`CImageList`所建立的物件[FromHandle](#fromhandle)，但不會終結任何控制代碼 ( `hImageList`) 暫時相關聯與**ImageList**物件。  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]  
  
##  <a name="detach"></a>CImageList::Detach  
 呼叫此函式可從影像清單物件卸離`CImageList`物件。  
  
```  
HIMAGELIST Detach();
```  
  
### <a name="return-value"></a>傳回值  
 影像清單物件控制代碼。  
  
### <a name="remarks"></a>備註  
 此函式傳回的控制代碼的影像清單物件。  
  
### <a name="example"></a>範例  
  請參閱範例的[CImageList::Attach](#attach)。  
  
##  <a name="dragenter"></a>CImageList::DragEnter  
 在拖曳作業時，會鎖定更新所指定視窗`pWndLock`，並顯示所指定的位置拖曳影像`point`。  
  
```  
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pWndLock`  
 擁有拖曳影像的視窗指標。  
  
 `point`  
 顯示拖曳影像的位置。 座標是相對於視窗 （非工作區） 的左上角。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 座標是相對於視窗左上角，因此指定座標時，您必須補償視窗項目，例如框線、 標題列和功能表列的寬度。  
  
 如果`pWndLock`是**NULL**、 這個函式桌面視窗中，與相關聯的顯示內容中繪製影像和座標是相對於螢幕左上角。  
  
 此函式在拖曳作業期間鎖定特定視窗的所有其他更新。 如果您需要在拖曳作業，例如反白顯示拖放作業的目標期間進行繪圖可以暫時隱藏被拖曳的影像使用[CImageList::DragLeave](#dragleave)函式。  
  
### <a name="example"></a>範例  
  請參閱範例的[CImageList::BeginDrag](#begindrag)。  
  
##  <a name="dragleave"></a>CImageList::DragLeave  
 解除鎖定由所指定視窗`pWndLock`並隱藏拖曳影像，讓 [更新] 視窗。  
  
```  
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```  
  
### <a name="parameters"></a>參數  
 `pWndLock`  
 擁有拖曳影像的視窗指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例的[CImageList::EndDrag](#enddrag)。  
  
##  <a name="dragmove"></a>CImageList::DragMove  
 呼叫此函式將拖放作業期間被拖曳的影像。  
  
```  
static BOOL PASCAL DragMove(CPoint pt);
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 新的拖曳位置。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式通常稱為以回應`WM_MOUSEMOVE`訊息。 若要開始拖曳作業，請使用`BeginDrag`成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]  
  
##  <a name="dragshownolock"></a>CImageList::DragShowNolock  
 顯示或隱藏在拖曳作業時，拖曳影像，而無需鎖定的視窗。  
  
```  
static BOOL PASCAL DragShowNolock(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 `bShow`  
 指定是否要顯示拖曳影像。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 [CImageList::DragEnter](#dragenter)函式在拖曳作業期間鎖定視窗的所有更新。 此函式，不過，不會鎖定視窗。  
  
##  <a name="draw"></a>Cimagelist:: Draw  
 呼叫此函式可繪製拖放作業期間被拖曳的影像。  
  
```  
BOOL Draw(
    CDC* pDC,  
    int nImage,  
    POINT pt,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 目的地裝置內容的指標。  
  
 `nImage`  
 要繪製之影像的以零為起始的索引。  
  
 `pt`  
 要繪製指定的裝置內容中的位置。  
  
 `nStyle`  
 旗標，指定繪製樣式。 它可以是下列其中一個或多個這些值：  
  
|值|意義|  
|-----------|-------------|  
|`ILD_BLEND25`**ILD_FOCUS**|繪製影像，混合使用系統醒目提示色彩的 25%。 如果影像清單不包含遮罩，此值沒有任何作用。|  
|`ILD_BLEND50`**ILD_SELECTED**， **ILD_BLEND**|繪製影像，混合使用系統醒目提示色彩的 50%。 如果影像清單不包含遮罩，此值沒有任何作用。|  
|**ILD_MASK**|繪製遮罩。|  
|`ILD_NORMAL`|繪製影像的影像清單中使用的背景色彩。 如果背景色彩是`CLR_NONE`以透明的方式使用遮罩繪製影像的值。|  
|`ILD_TRANSPARENT`|繪製影像以透明的方式使用遮罩，不論的背景色彩。|  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例的[cimagelist:: Setoverlayimage](#setoverlayimage)。  
  
##  <a name="drawex"></a>CImageList::DrawEx  
 指定的裝置內容中繪製的映像清單項目。  
  
```  
BOOL DrawEx(
    CDC* pDC,  
    int nImage,  
    POINT pt,  
    SIZE sz,  
    COLORREF clrBk,  
    COLORREF clrFg,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 目的地裝置內容的指標。  
  
 `nImage`  
 要繪製之影像的以零為起始的索引。  
  
 `pt`  
 要繪製指定的裝置內容中的位置。  
  
 `sz`  
 要繪製影像的左上角相對的影像部分的大小。 請參閱`dx`和*dy*中[ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) Windows SDK 中。  
  
 *clrBk*  
 映像的背景色彩。 請參閱*rgbBk*中[ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) Windows SDK 中。  
  
 *clrFg*  
 映像的前景色彩。 請參閱*rgbFg*中[ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) Windows SDK 中。  
  
 `nStyle`  
 旗標，指定繪製樣式。 請參閱*fStyle*中[ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536) Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 函式會使用指定的繪製樣式，並混合的映像，以指定的色彩。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]  
  
##  <a name="drawindirect"></a>CImageList::DrawIndirect  
 呼叫此成員函式，從影像清單繪製影像。  
  
```  
BOOL DrawIndirect(IMAGELISTDRAWPARAMS* pimldp);

 
BOOL DrawIndirect(
    CDC* pDC,  
    int nImage,  
    POINT pt,  
    SIZE sz,  
    POINT ptOrigin,  
    UINT fStyle = ILD_NORMAL,  
    DWORD dwRop = SRCCOPY,  
    COLORREF rgbBack = CLR_DEFAULT,  
    COLORREF rgbFore = CLR_DEFAULT,  
    DWORD fState = ILS_NORMAL,  
    DWORD Frame = 0,  
    COLORREF crEffect = CLR_DEFAULT);
```  
  
### <a name="parameters"></a>參數  
 *pimldp*  
 指標[IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395)結構，其中包含繪圖作業的相關資訊。  
  
 `pDC`  
 目的地裝置內容的指標。 您必須刪除此[CDC](../../mfc/reference/cdc-class.md)物件與它完成時。  
  
 `nImage`  
 要繪製影像的以零為起始的索引。  
  
 `pt`  
 A[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)結構，其中包含 x 和 y 座標來繪製影像。  
  
 `sz`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)結構，表示要繪製影像的大小。  
  
 *ptOrigin*  
 A[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)包含 x 和 y 座標指定左上的角相對於映像本身繪圖作業的結構。 不會繪製影像的左邊的 x 座標和 y 軸上方的像素。  
  
 `fStyle`  
 旗標，指定繪製樣式，並選擇性地將重疊影像。 將重疊影像上，請參閱 < 備註 > 一節的資訊。 MFC 預設實作、 `ILD_NORMAL`，繪製影像的影像清單中使用的背景色彩。 如果背景色彩是`CLR_NONE`繪製影像的值，以透明的方式使用遮罩。  
  
 其他可能的樣式會下所述**fStyle**隸屬[IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395)結構。  
  
 *dwRop*  
 值，指定的點陣作業程式碼。 這些程式碼會定義來源矩形的色彩資料目的地矩形來達成的完稿色彩的色彩資料的合併方式。 MFC 的預設實作， **SRCCOPY**，複製到目的地矩形的直接來源矩形。 這個參數已忽略如果`fStyle`參數不包括**ILD_ROP**旗標。  
  
 其他可能的值底下所述**dwRop**隸屬[IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395)結構。  
  
 *rgbBack*  
 映像的背景色彩，根據預設`CLR_DEFAULT`。 這個參數可以是應用程式定義的 RGB 值，或下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|`CLR_DEFAULT`|預設背景色彩。 使用影像清單的背景色彩繪製影像。|  
|`CLR_NONE`|沒有背景色彩。 以透明的方式繪製影像。|  
  
 *rgbFore*  
 映像預設前景色彩`CLR_DEFAULT`。 這個參數可以是應用程式定義的 RGB 值，或下列值之一：  
  
|值|意義|  
|-----------|-------------|  
|`CLR_DEFAULT`|預設前景色彩。 使用系統醒目提示色彩為前景色彩來繪製影像。|  
|`CLR_NONE`|Blend 色彩。 影像會與目的地裝置內容的色彩混合。|  
  
 只有當使用這個參數`fStyle`包含`ILD_BLEND25`或`ILD_BLEND50`旗標。  
  
 *fState*  
 指定繪製狀態旗標。 這個成員可以包含一或多個映像清單狀態旗標。  
  
 *Frame*  
 會影響 saturate 和 alpha 透明混色效果的行為。  
  
 當搭配**ILS_SATURATE**，這個成員會保有加入 RGB 數，每個像素圖示中的每個色彩元件的值。  
  
 當搭配**ILS_APLHA**，這個成員保留 alpha 色板的值。 這個值可以介於 0 到 255，0 表示完全透明，而且 255 完全不透明。  
  
 *crEffect*  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)光暈和陰影效果所使用的值。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**如果映像已成功地繪製否則**FALSE**。  
  
### <a name="remarks"></a>備註  
 如果您想要自行填入 Win32 結構，請使用第一個版本。 如果您想要充分利用一或多個 MFC 的預設引數，或避免管理結構，請使用第二個版本。  
  
 覆疊影像是繪製在主要映像，這個成員函式中指定之上的映像`nImage`參數。 使用來繪製覆疊遮罩[繪製](#draw)成員函式，以 1 為基底的索引使用指定的覆疊遮罩[INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408)巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]  
  
##  <a name="enddrag"></a>CImageList::EndDrag  
 呼叫此函式來結束拖曳作業。  
  
```  
static void PASCAL EndDrag();
```  
  
### <a name="remarks"></a>備註  
 若要開始拖曳作業，請使用`BeginDrag`成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]  
  
##  <a name="extracticon"></a>CImageList::ExtractIcon  
 呼叫此函式可建立為基礎的映像和其相關的遮罩影像清單中的圖示。  
  
```  
HICON ExtractIcon(int nImage);
```  
  
### <a name="parameters"></a>參數  
 `nImage`  
 映像的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功; 圖示的控制代碼否則**NULL**。  
  
### <a name="remarks"></a>備註  
 這個方法會依賴的行為[ImageList_ExtractIcon](http://msdn.microsoft.com/library/windows/desktop/bb761401)巨集，以建立圖示。 請參閱[ImageList_ExtractIcon](http://msdn.microsoft.com/library/windows/desktop/bb761401)巨集，如需詳細資訊，圖示的建立和清除。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]  
  
##  <a name="fromhandle"></a>CImageList::FromHandle  
 將指標傳回至`CImageList`物件時提供影像清單控制代碼。  
  
```  
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>參數  
 `hImageList`  
 指定映像清單。  
  
### <a name="return-value"></a>傳回值  
 指標`CImageList`物件，如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果`CImageList`尚未附加至控制代碼，暫存`CImageList`物件會建立並附加。 此暫存`CImageList`物件是否有效，僅直到下一次應用程式有其事件迴圈中的閒置時間，在哪個階段所有暫存物件被刪除。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]  
  
##  <a name="fromhandlepermanent"></a>CImageList::FromHandlePermanent  
 將指標傳回至`CImageList`物件時提供影像清單控制代碼。  
  
```  
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>參數  
 `hImageList`  
 指定映像清單。  
  
### <a name="return-value"></a>傳回值  
 指標`CImageList`物件，如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果`CImageList`物件沒有附加至控制代碼， **NULL**傳回。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]  
  
##  <a name="getbkcolor"></a>CImageList::GetBkColor  
 呼叫此函式可擷取影像清單目前的背景色彩。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 RGB 色彩值`CImageList`物件背景色彩。  
  
### <a name="example"></a>範例  
  請參閱範例的[CImageList::SetBkColor](#setbkcolor)。  
  
##  <a name="getdragimage"></a>CImageList::GetDragImage  
 取得用於拖曳暫存影像清單。  
  
```  
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,  
    LPPOINT lpPointHotSpot);
```  
  
### <a name="parameters"></a>參數  
 `lpPoint`  
 位址[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)結構接收目前拖曳位置。  
  
 *lpPointHotSpot*  
 位址**點**結構接收拖曳影像相對於拖曳位置的位移。  
  
### <a name="return-value"></a>傳回值  
 如果成功，指向暫存影像的清單，用於拖曳;否則， **NULL**。  
  
##  <a name="getimagecount"></a>CImageList::GetImageCount  
 呼叫此函式可擷取的影像清單中的影像數目。  
  
```  
int GetImageCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 映像數目。  
  
### <a name="example"></a>範例  
  請參閱範例的[CImageList::ExtractIcon](#extracticon)。  
  
##  <a name="getimageinfo"></a>CImageList::GetImageInfo  
 呼叫此函式可擷取映像的相關資訊。  
  
```  
BOOL GetImageInfo(
    int nImage,  
    IMAGEINFO* pImageInfo) const;  
```  
  
### <a name="parameters"></a>參數  
 `nImage`  
 映像的以零為起始的索引。  
  
 *pImageInfo*  
 指標[IMAGEINFO](http://msdn.microsoft.com/library/windows/desktop/bb761393)接收映像的相關資訊的結構。 在此結構中的資訊可以用來直接操作影像的點陣圖。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 `IMAGEINFO`結構包含一個影像清單中的映像的相關資訊。  
  
##  <a name="getsafehandle"></a>CImageList::GetSafeHandle  
 呼叫此函式可擷取**m_hImageList**資料成員。  
  
```  
HIMAGELIST GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 附加的影像清單控制代碼否則**NULL**如果附加的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]  
  
##  <a name="m_himagelist"></a>CImageList::m_hImageList  
 附加至這個物件的影像清單控制代碼。  
  
 **HIMAGELIST m_hImageList;**  
  
### <a name="remarks"></a>備註  
 **M_hImageList**資料成員是類型的公用變數`HIMAGELIST`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]  
  
##  <a name="operator_himagelist"></a>CImageList::operator HIMAGELIST  
 使用此運算子，以取得附加的控制代碼的`CImageList`物件。  
  
```  
operator HIMAGELIST() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，影像清單控制代碼來表示`CImageList`物件; 否則**NULL**。  
  
### <a name="remarks"></a>備註  
 這位操作員便轉型運算子，可支援直接使用`HIMAGELIST`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]  
  
##  <a name="read"></a>CImageList::Read  
 呼叫此函式可從封存讀取影像清單。  
  
```  
BOOL Read(CArchive* pArchive);
```  
  
### <a name="parameters"></a>參數  
 `pArchive`  
 指標`CArchive`從中影像清單是要讀取的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]  
  
##  <a name="remove"></a>CImageList::Remove  
 呼叫此函式可從影像清單物件中移除映像。  
  
```  
BOOL Remove(int nImage);
```  
  
### <a name="parameters"></a>參數  
 `nImage`  
 要移除之影像的以零為起始索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 之後的所有項目`nImage`現在下移一個位置。 例如，如果影像清單包含兩個項目，刪除第一個項目會導致要現在會在第一個位置中的剩餘項目。 `nImage`= 0，第一個位置中的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]  
  
##  <a name="replace"></a>CImageList::Replace  
 呼叫此函式可利用新影像取代影像清單中的映像。  
  
```  
BOOL Replace(
    int nImage,  
    CBitmap* pbmImage,  
    CBitmap* pbmMask);

 
int Replace(
    int nImage,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>參數  
 `nImage`  
 要取代之影像的以零為起始索引。  
  
 `pbmImage`  
 指標，包含影像的點陣圖。  
  
 `pbmMask`  
 包含遮罩點陣圖指標。 如果沒有遮罩影像清單搭配使用，則會忽略這個參數。  
  
 `hIcon`  
 包含點陣圖和新的映像的遮罩之圖示的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回的版本**BOOL**傳回非零，如果成功，則為，否則為 0。  
  
 傳回的版本`int`傳回映像的以零為起始的索引; 如果成功，否則為-1。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式之後呼叫[SetImageCount](#setimagecount)若要指派新，有效的映像以預留位置影像的索引編號。  
  
### <a name="example"></a>範例  
  請參閱範例的[CImageList::SetImageCount](#setimagecount)。  
  
##  <a name="setbkcolor"></a>CImageList::SetBkColor  
 呼叫此函式可設定影像清單的背景色彩。  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>參數  
 `cr`  
 若要設定的背景色彩。 它可以是`CLR_NONE`。 在此情況下，影像會繪製以透明的方式使用遮罩。  
  
### <a name="return-value"></a>傳回值  
 先前的背景色彩如果登錄成功。否則`CLR_NONE`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]  
  
##  <a name="setdragcursorimage"></a>CImageList::SetDragCursorImage  
 建立新的拖曳影像合併指定的影像 （通常是滑鼠游標影像） 與目前拖曳影像。  
  
```  
BOOL SetDragCursorImage(
    int nDrag,  
    CPoint ptHotSpot);
```  
  
### <a name="parameters"></a>參數  
 *nDrag*  
 新的映像，以結合拖曳影像的索引。  
  
 `ptHotSpot`  
 作用中新的映像的位置。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 由於拖曳函式在拖曳作業期間使用新的映像，您應該使用 Windows [ShowCursor](http://msdn.microsoft.com/library/windows/desktop/ms648396)函式呼叫之後隱藏實際滑鼠游標`CImageList::SetDragCursorImage`。 否則，系統可能會在拖曳作業期間出現兩個滑鼠游標。  
  
##  <a name="setimagecount"></a>CImageList::SetImageCount  
 呼叫此成員函式中的映像數目重設`CImageList`物件。  
  
```  
BOOL SetImageCount(UINT uNewCount);
```  
  
### <a name="parameters"></a>參數  
 *uNewCount*  
 影像清單中指定新的映像總數的值。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您呼叫此成員函式，以增加影像清單中的影像數目，然後呼叫[取代](#replace)每個其他映像以將新的索引指派給有效的映像。 如果您無法將索引指派給有效的映像，建立新的映像的繪製作業將無法預測結果。  
  
 如果您使用此函式來減少映像清單的大小，會釋放已截斷映像。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]  
  
##  <a name="setoverlayimage"></a>Cimagelist:: Setoverlayimage  
 呼叫此函式可用於覆疊遮罩的影像清單中加入影像之以零為起始的索引。  
  
```  
BOOL SetOverlayImage(
    int nImage,  
    int nOverlay);
```  
  
### <a name="parameters"></a>參數  
 `nImage`  
 要當做覆疊遮罩的影像以零為起始的索引。  
  
 *nOverlay*  
 1 為基底覆疊遮罩的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 最多四個索引也可以加入至清單。  
  
 覆疊遮罩是透過另一個映像以透明方式繪製影像。 使用在影像上繪製覆疊遮罩[cimagelist:: Draw](#draw)成員函式，以 1 為基底的索引使用指定的覆疊遮罩**INDEXTOOVERLAYMASK**巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]  
  
##  <a name="write"></a>CImageList::Write  
 呼叫此函式來寫入封存中的影像清單物件。  
  
```  
BOOL Write(CArchive* pArchive);
```  
  
### <a name="parameters"></a>參數  
 `pArchive`  
 指標`CArchive`影像清單為儲存的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CListCtrl 類別](../../mfc/reference/clistctrl-class.md)   
 [CTabCtrl 類別](../../mfc/reference/ctabctrl-class.md)
