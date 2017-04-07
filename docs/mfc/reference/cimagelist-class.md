---
title: "CImageList 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [C++], CImageList
- image lists [C++], CImageList class
- CImageList class
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
caps.latest.revision: 19
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
ms.openlocfilehash: e61d99d6d68b1c68cd5e306dd0fcd10d6fe4324d
ms.lasthandoff: 02/24/2017

---
# <a name="cimagelist-class"></a>CImageList 類別
提供 Windows 通用影像清單控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CImageList : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CImageList::CImageList](#cimagelist)|建構 `CImageList` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CImageList::Add](#add)|將影像清單的映像或映像。|  
|[CImageList::Attach](#attach)|附加影像清單至`CImageList`物件。|  
|[CImageList::BeginDrag](#begindrag)|開始拖曳影像。|  
|[CImageList::Copy](#copy)|將映像內複製`CImageList`物件。|  
|[CImageList::Create](#create)|初始化影像清單，並將它附加`CImageList`物件。|  
|[CImageList::DeleteImageList](#deleteimagelist)|刪除映像清單。|  
|[CImageList::DeleteTempMap](#deletetempmap)|由呼叫[CWinApp](../../mfc/reference/cwinapp-class.md)閒置時間處理常式，以刪除任何暫存`CImageList`所建立物件`FromHandle`。|  
|[CImageList::Detach](#detach)|中斷連結的影像清單物件，從`CImageList`物件，並將控制代碼傳回至映像清單。|  
|[CImageList::DragEnter](#dragenter)|在拖曳作業期間鎖定更新，並顯示拖曳影像的指定位置。|  
|[CImageList::DragLeave](#dragleave)|解除鎖定 視窗，並隱藏拖曳影像，讓視窗可更新。|  
|[CImageList::DragMove](#dragmove)|移動拖放作業期間被拖曳的影像。|  
|[CImageList::DragShowNolock](#dragshownolock)|顯示或隱藏在拖曳作業時，拖曳影像，而不鎖定視窗。|  
|[Cimagelist:: Draw](#draw)|繪製拖放作業期間被拖曳的影像。|  
|[CImageList::DrawEx](#drawex)|在指定的裝置內容中繪製影像清單項目。 函式會使用指定的繪製樣式，並混合使用指定的色彩為影像。|  
|[CImageList::DrawIndirect](#drawindirect)|繪製影像的影像清單中。|  
|[CImageList::EndDrag](#enddrag)|結束在拖曳作業。|  
|[CImageList::ExtractIcon](#extracticon)|建立基礎的影像和遮罩影像清單中的圖示。|  
|[CImageList::FromHandle](#fromhandle)|若要將指標傳回`CImageList`物件提供影像清單控制代碼時。 如果 `CImageList` 物件沒有附加至控制代碼，會建立並附加暫存 `CImageList` 物件。|  
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|若要將指標傳回`CImageList`物件提供影像清單控制代碼時。 如果`CImageList`物件沒有附加至控制代碼， **NULL**傳回。|  
|[CImageList::GetBkColor](#getbkcolor)|擷取目前的影像清單的背景色彩。|  
|[CImageList::GetDragImage](#getdragimage)|取得用於拖曳暫存影像清單。|  
|[CImageList::GetImageCount](#getimagecount)|擷取映像清單中的映像的數目。|  
|[CImageList::GetImageInfo](#getimageinfo)|擷取映像的相關資訊。|  
|[CImageList::GetSafeHandle](#getsafehandle)|擷取**m_hImageList**。|  
|[CImageList::Read](#read)|從封存讀取影像清單。|  
|[CImageList::Remove](#remove)|從影像清單中移除映像。|  
|[CImageList::Replace](#replace)|影像清單中的映像取代成新的映像。|  
|[CImageList::SetBkColor](#setbkcolor)|設定影像清單的背景色彩。|  
|[CImageList::SetDragCursorImage](#setdragcursorimage)|建立新的拖曳影像。|  
|[CImageList::SetImageCount](#setimagecount)|重設影像清單中的映像的計數。|  
|[Cimagelist:: Setoverlayimage](#setoverlayimage)|將影像之以零為起始的索引加入至當做覆疊遮罩的映像的清單。|  
|[CImageList::Write](#write)|寫入封存檔中的影像清單。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CImageList::operator HIMAGELIST](#operator_himagelist)|傳回`HIMAGELIST`附加至`CImageList`。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CImageList::m_hImageList](#m_himagelist)|包含附加至這個物件的影像清單控制代碼。|  
  
## <a name="remarks"></a>備註  
 「 映像清單 」 是相同大小的影像，其中每一個可以參考由其以零為起始的索引集合。 影像清單用來有效管理大量圖示或點陣圖。 影像清單中的所有影像會都包含在單一的寬點陣圖中螢幕裝置格式。 影像清單也可以包括一個包含遮罩 (用來以透明方式繪製影像) 的單色點陣圖 (圖示樣式)。 Microsoft Win32 應用程式發展介面 (API) 提供可讓您繪製影像、 建立和終結影像清單、 新增和移除影像、 取代影像、 合併影像和拖曳影像的影像清單函式。  
  
 這個控制項 (並因此`CImageList`類別) 僅適用於執行 Windows 95/98 和 Windows NT 版本 3.51 下的程式和更新版本。  
  
 如需有關使用`CImageList`，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CImageList](../../mfc/using-cimagelist.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CImageList`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="add"></a>CImageList::Add  
 呼叫此函式可將一或多個映像或圖示加入至影像清單。  
  
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
 包含影像的點陣圖的指標。 從點陣圖的寬度推斷的映像數目。  
  
 `pbmMask`  
 包含遮罩點陣圖的指標。 如果未遮罩影像清單與使用時，會忽略此參數。  
  
 `crMask`  
 用來產生遮罩的色彩。 此色彩指定點陣圖中的每個像素會變成黑色，以及對應的位元遮罩中設為一。  
  
 `hIcon`  
 包含點陣圖和新的映像的遮罩之圖示的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功，第一個新影像的以零起始的索引否則為-1。  
  
### <a name="remarks"></a>備註  
 您必須負責釋放圖示的控制代碼，當您在使用它。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&1;](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]  
  
##  <a name="attach"></a>CImageList::Attach  
 呼叫此函式附加影像清單至`CImageList`物件。  
  
```  
BOOL Attach(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>參數  
 `hImageList`  
 影像清單物件控制代碼。  
  
### <a name="return-value"></a>傳回值  
 附件成功; 如果為非零否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&2;](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]  
  
##  <a name="begindrag"></a>CImageList::BeginDrag  
 呼叫此函式開始拖曳影像。  
  
```  
BOOL BeginDrag(
    int nImage,  
    CPoint ptHotSpot);
```  
  
### <a name="parameters"></a>參數  
 `nImage`  
 要拖曳的影像的以零為起始的索引。  
  
 `ptHotSpot`  
 開始拖放到位置 （一般而言，資料指標位置） 的座標。 座標是相對於映像的左上角。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式會建立用於將暫存的影像清單。 映像結合目前的資料指標指定的映像和其遮罩。 在後續回應`WM_MOUSEMOVE`訊息，您可以利用移動拖曳影像`DragMove`成員函式。 若要結束拖曳作業時，您可以使用`EndDrag`成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&3;](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]  
  
##  <a name="cimagelist"></a>CImageList::CImageList  
 建構 `CImageList` 物件。  
  
```  
CImageList();
```  
  
##  <a name="copy"></a>CImageList::Copy  
 此成員函式實作的 Win32 函式的行為[ImageList_Copy](http://msdn.microsoft.com/library/windows/desktop/bb761520)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
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
 要做為複製作業的目的地映像的以零為起始的索引。  
  
 `iSrc`  
 要做為複製作業的來源映像的以零為起始的索引。  
  
 `uFlags`  
 位元旗標值，指定進行複製作業的型別。 這個參數可以是下列值之一︰  
  
|值|意義|  
|-----------|-------------|  
|`ILCF_MOVE`|來源映像會複製到目的地映像的索引。 這項作業會產生指定之影像的多個執行個體。 `ILCF_MOVE` 是預設值。|  
|`ILCF_SWAP`|來源和目的地影像交換影像清單中的位置。|  
  
 `pSrc`  
 指標`CImageList`複製作業的目標物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&6;](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]  
  
##  <a name="create"></a>CImageList::Create  
 初始化影像清單，並將它附加[CImageList](../../mfc/reference/cimagelist-class.md)物件。  
  
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
 每個影像，單位為像素的維度。  
  
 `cy`  
 每個影像，單位為像素的維度。  
  
 `nFlags`  
 指定要建立的映像清單的類型。 這個參數可以是下列值的組合，但它可以包含的其中之一`ILC_COLOR`值。  
  
|值|意義|  
|-----------|-------------|  
|`ILC_COLOR`|使用預設行為，如果沒有其他`ILC_COLOR`* 指定旗標。 一般來說，預設值是`ILC_COLOR4`; 但較舊的顯示驅動程式的預設值是`ILC_COLORDDB`。|  
|`ILC_COLOR4`|作為 4 位元 （16 色） 與裝置無關點陣圖 (DIB) 區段點陣圖影像清單。|  
|`ILC_COLOR8`|使用 8 位元 DIB 區段。 色彩資料表所使用的色彩為相同的半色調調色盤的色彩。|  
|`ILC_COLOR16`|使用 16 位元 (32/64 k 色彩) DIB 區段。|  
|`ILC_COLOR24`|使用 24 位元 DIB 區段。|  
|`ILC_COLOR32`|使用 32 位元 DIB 區段。|  
|`ILC_COLORDDB`|使用裝置相關點陣圖。|  
|`ILC_MASK`|使用遮罩。 影像清單包含兩個點陣圖，其中是當做遮罩的單色點陣圖。 不包含此值時，影像清單包含只有一個點陣圖。 請參閱[繪製影像，從影像清單](../../mfc/drawing-images-from-an-image-list.md)如需有關遮罩的影像。|  
  
 `nInitial`  
 一開始只包含影像清單的影像數目。  
  
 `nGrow`  
 依據系統需要調整大小以讓出空間給新的映像清單時，所能成長的影像清單的映像數目。 這個參數代表已調整大小的影像清單可包含的新映像的數目。  
  
 `nBitmapID`  
 資源識別碼的點陣圖影像清單與相關聯。  
  
 `crMask`  
 用來產生遮罩的色彩。 此色彩在指定的點陣圖中的每個像素會變成黑色，以及對應的位元遮罩中設為一。  
  
 `lpszBitmapID`  
 字串，包含資源的映像的識別碼。  
  
 `imagelist1`  
 對 `CImageList` 物件的參考。  
  
 `nImage1`  
 第一個現有的映像的索引。  
  
 `imagelist2`  
 對 `CImageList` 物件的參考。  
  
 `nImage2`  
 第二個現有的映像的索引。  
  
 `dx`  
 第二個影像像素為單位的第一個影像的關聯性的 x 軸的位移。  
  
 `dy`  
 第二個影像像素為單位的第一個影像的關聯性的 y 軸的位移。  
  
 `pImageList`  
 指標`CImageList`物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 您建構`CImageList`兩個步驟。 首先，呼叫建構函式，接著呼叫`Create`，這會建立影像清單，並將其以附加`CImageList`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&7;](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]  
  
##  <a name="deleteimagelist"></a>CImageList::DeleteImageList  
 呼叫此函式來刪除影像清單。  
  
```  
BOOL DeleteImageList();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&8;](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]  
  
##  <a name="deletetempmap"></a>CImageList::DeleteTempMap  
 自動呼叫`CWinApp`閒置時間處理常式，`DeleteTempMap`會刪除任何暫存`CImageList`所建立的物件[FromHandle](#fromhandle)，但不會終結任何控制代碼 ( `hImageList`) 暫時聯**ImageList**物件。  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&9;](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]  
  
##  <a name="detach"></a>CImageList::Detach  
 呼叫此函式可卸離的影像清單物件，從`CImageList`物件。  
  
```  
HIMAGELIST Detach();
```  
  
### <a name="return-value"></a>傳回值  
 影像清單物件控制代碼。  
  
### <a name="remarks"></a>備註  
 此函式傳回的控制代碼的影像清單物件。  
  
### <a name="example"></a>範例  
  請參閱範例[CImageList::Attach](#attach)。  
  
##  <a name="dragenter"></a>CImageList::DragEnter  
 在拖曳作業時，鎖定更新所指定視窗`pWndLock`，並顯示所指定的位置拖曳影像`point`。  
  
```  
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,  
    CPoint point);
```  
  
### <a name="parameters"></a>參數  
 `pWndLock`  
 主控視窗的拖曳影像的指標。  
  
 `point`  
 用來顯示拖曳影像的位置。 座標是相對於視窗 （而非工作區） 的左上角。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 座標是相對於視窗左上角，以便指定座標時，您必須補償視窗項目，例如框線、 標題列和功能表列的寬度。  
  
 如果`pWndLock`是**NULL**、 這個函式與桌面視窗相關聯的顯示內容中繪製影像和座標是相對於螢幕左上角。  
  
 此函式在拖曳作業期間鎖定特定視窗的其他更新。 如果您需要執行任何繪圖在拖曳作業時，例如反白顯示拖放作業的目標可以暫時隱藏被拖曳的影像使用[CImageList::DragLeave](#dragleave)函式。  
  
### <a name="example"></a>範例  
  請參閱範例[CImageList::BeginDrag](#begindrag)。  
  
##  <a name="dragleave"></a>CImageList::DragLeave  
 解除鎖定所指定的視窗`pWndLock`，並隱藏拖曳影像，讓 [更新] 視窗。  
  
```  
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```  
  
### <a name="parameters"></a>參數  
 `pWndLock`  
 主控視窗的拖曳影像的指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例[CImageList::EndDrag](#enddrag)。  
  
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
 此函式通常稱為以回應`WM_MOUSEMOVE`訊息。 若要開始拖曳作業時，使用`BeginDrag`成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&4;](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]  
  
##  <a name="dragshownolock"></a>CImageList::DragShowNolock  
 顯示或隱藏在拖曳作業時，拖曳影像，而不鎖定視窗。  
  
```  
static BOOL PASCAL DragShowNolock(BOOL bShow);
```  
  
### <a name="parameters"></a>參數  
 `bShow`  
 指定是否要顯示的拖曳影像。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 [CImageList::DragEnter](#dragenter)函式在拖曳作業期間鎖定視窗的所有更新。 這個函式，不過，不會鎖定視窗。  
  
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
 目的地裝置內容指標。  
  
 `nImage`  
 要繪製之影像的以零為起始的索引。  
  
 `pt`  
 在要繪製指定的裝置內容中的位置。  
  
 `nStyle`  
 旗標，指定繪製樣式。 它可以是下列其中一個或多個這些值︰  
  
|值|意義|  
|-----------|-------------|  
|`ILD_BLEND25`**ILD_FOCUS**|繪製影像，混合使用系統醒目提示色彩的 25%。 如果影像清單不包含遮罩，這個值會有任何作用。|  
|`ILD_BLEND50`**ILD_SELECTED**， **ILD_BLEND**|繪製影像，混合使用系統醒目提示色彩的 50%。 如果影像清單不包含遮罩，這個值會有任何作用。|  
|**ILD_MASK**|繪製遮罩。|  
|`ILD_NORMAL`|繪製影像的影像清單中使用的背景色彩。 如果背景色彩是`CLR_NONE`無障礙地使用遮罩繪製影像的值。|  
|`ILD_TRANSPARENT`|繪製影像的透明地使用遮罩，不論背景色彩。|  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例[cimagelist:: Setoverlayimage](#setoverlayimage)。  
  
##  <a name="drawex"></a>CImageList::DrawEx  
 在指定的裝置內容中繪製影像清單項目。  
  
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
 目的地裝置內容指標。  
  
 `nImage`  
 要繪製之影像的以零為起始的索引。  
  
 `pt`  
 在要繪製指定的裝置內容中的位置。  
  
 `sz`  
 要繪製影像左上角相對的影像部分的大小。 請參閱`dx`和*dy*中[ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 *clrBk*  
 映像的背景色彩。 請參閱*rgbBk*中[ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 *clrFg*  
 映像的前景色彩。 請參閱*rgbFg*中[ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 `nStyle`  
 旗標，指定繪製樣式。 請參閱*fStyle*中[ImageList_DrawEx](http://msdn.microsoft.com/library/windows/desktop/bb761536)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 函式會使用指定的繪製樣式，並混合使用指定的色彩為影像。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&10;](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]  
  
##  <a name="drawindirect"></a>CImageList::DrawIndirect  
 呼叫此成員函式，從影像清單中繪製影像。  
  
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
 目的地裝置內容指標。 您必須刪除此[CDC](../../mfc/reference/cdc-class.md)物件時用完。  
  
 `nImage`  
 要繪製影像的以零為起始的索引。  
  
 `pt`  
 A[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)結構，其中包含 x – 和 y-座標來繪製影像。  
  
 `sz`  
 A[大小](http://msdn.microsoft.com/library/windows/desktop/dd145106)結構，表示要繪製影像的大小。  
  
 *ptOrigin*  
 A[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)結構，其中包含 x – 和 y-座標指定相對於映像本身繪圖作業的左上的角。 不會繪製影像的 – x 座標和 y-座標上方左邊的像素。  
  
 `fStyle`  
 旗標，指定繪製樣式，並選擇性地覆疊影像。 在覆疊影像，請參閱 < 備註 > 一節，以資訊。 MFC 預設實作中， `ILD_NORMAL`，繪製影像的影像清單中使用的背景色彩。 如果背景色彩是`CLR_NONE`無障礙地使用遮罩繪製影像的值。  
  
 其他可能的樣式說明下**fStyle**成員[IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395)結構。  
  
 *dwRop*  
 值，指定的點陣作業程式碼。 這些程式碼會定義如何將來源矩形的色彩資料結合達成最終色彩目的地矩形的色彩資料。 MFC 的預設實作， **SRCCOPY**，複製到目的地矩形的直接來源矩形。 如果這個參數就會忽略`fStyle`參數不包含**ILD_ROP**旗標。  
  
 其他可能的值描述在**dwRop**成員[IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395)結構。  
  
 *rgbBack*  
 映像的背景色彩，根據預設`CLR_DEFAULT`。 這個參數可以是應用程式定義的 RGB 值，或下列值之一︰  
  
|值|意義|  
|-----------|-------------|  
|`CLR_DEFAULT`|預設背景色彩。 使用影像清單的背景色彩來繪製影像。|  
|`CLR_NONE`|沒有背景色彩。 以透明方式繪製影像。|  
  
 *rgbFore*  
 映像預設前景色彩`CLR_DEFAULT`。 這個參數可以是應用程式定義的 RGB 值，或下列值之一︰  
  
|值|意義|  
|-----------|-------------|  
|`CLR_DEFAULT`|預設前景色彩。 使用系統醒目提示色彩為前景色彩來繪製影像。|  
|`CLR_NONE`|沒有 blend 色彩。 映像會與目的地裝置內容的色彩混合。|  
  
 只有當使用這個參數`fStyle`包含`ILD_BLEND25`或`ILD_BLEND50`旗標。  
  
 *fState*  
 旗標，指定繪製的狀態。 這個成員可以包含一或多個映像清單狀態旗標。  
  
 *框架*  
 會影響 saturate 和 alpha 混色效果的行為。  
  
 當搭配**ILS_SATURATE**，這個成員保存加入 RGB 一體，每個像素圖示中的每個色彩元件的值。  
  
 當搭配**ILS_APLHA**，這個成員會保留 alpha 色頻的值。 這個值可以介於 0 到 255，0 表示完全透明，且 255 完全不透明。  
  
 *crEffect*  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)用於光暈和陰影效果的值。  
  
### <a name="return-value"></a>傳回值  
 **TRUE**映像已成功地繪製，否則如果**FALSE**。  
  
### <a name="remarks"></a>備註  
 如果您想要自行填入 Win32 結構，請使用第一個版本。 如果您想要充分利用一或多個 MFC 的預設引數，或避免管理結構，請使用第二個版本。  
  
 覆疊影像是繪製在主要映像，此成員函式中指定的映像`nImage`參數。 繪製覆疊遮罩使用[繪製](#draw)起始的索引，使用指定的覆疊遮罩的成員函式[INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408)巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&11;](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]  
  
##  <a name="enddrag"></a>CImageList::EndDrag  
 呼叫此函式來結束在拖曳作業。  
  
```  
static void PASCAL EndDrag();
```  
  
### <a name="remarks"></a>備註  
 若要開始拖曳作業時，使用`BeginDrag`成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&5;](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]  
  
##  <a name="extracticon"></a>CImageList::ExtractIcon  
 呼叫此函式來建立基礎映像和其相關的遮罩影像清單中的圖示。  
  
```  
HICON ExtractIcon(int nImage);
```  
  
### <a name="parameters"></a>參數  
 `nImage`  
 映像的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功，圖示的控制代碼否則**NULL**。  
  
### <a name="remarks"></a>備註  
 這個方法依賴的行為[ImageList_ExtractIcon](http://msdn.microsoft.com/library/windows/desktop/bb761401)巨集，以建立圖示。 請參閱[ImageList_ExtractIcon](http://msdn.microsoft.com/library/windows/desktop/bb761401)巨集，如需有關圖示建立和清除。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&12;](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]  
  
##  <a name="fromhandle"></a>CImageList::FromHandle  
 若要將指標傳回`CImageList`物件提供影像清單控制代碼時。  
  
```  
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>參數  
 `hImageList`  
 指定映像清單。  
  
### <a name="return-value"></a>傳回值  
 指標`CImageList`物件如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果`CImageList`尚未附加至控制代碼，暫存`CImageList`會建立並附加物件。 此暫存`CImageList`僅直到下一次應用程式在其事件迴圈中有閒置時間，屆時所有暫存物件被刪除，物件才有效。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&13;](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]  
  
##  <a name="fromhandlepermanent"></a>CImageList::FromHandlePermanent  
 若要將指標傳回`CImageList`物件提供影像清單控制代碼時。  
  
```  
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>參數  
 `hImageList`  
 指定映像清單。  
  
### <a name="return-value"></a>傳回值  
 指標`CImageList`物件如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果`CImageList`物件沒有附加至控制代碼， **NULL**傳回。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&14;](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]  
  
##  <a name="getbkcolor"></a>CImageList::GetBkColor  
 呼叫此函式可擷取目前的影像清單的背景色彩。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 RGB 色彩值的`CImageList`物件背景色彩。  
  
### <a name="example"></a>範例  
  請參閱範例[CImageList::SetBkColor](#setbkcolor)。  
  
##  <a name="getdragimage"></a>CImageList::GetDragImage  
 取得用於拖曳暫存影像清單。  
  
```  
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,  
    LPPOINT lpPointHotSpot);
```  
  
### <a name="parameters"></a>參數  
 `lpPoint`  
 位址[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)結構會接收目前拖曳位置。  
  
 *lpPointHotSpot*  
 位址**點**結構會接收拖曳影像相對於拖曳位置的位移。  
  
### <a name="return-value"></a>傳回值  
 如果成功，指向暫存映像的清單，用於拖曳。否則， **NULL**。  
  
##  <a name="getimagecount"></a>CImageList::GetImageCount  
 呼叫此函式可擷取的映像清單中的映像數目。  
  
```  
int GetImageCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 映像數目。  
  
### <a name="example"></a>範例  
  請參閱範例[CImageList::ExtractIcon](#extracticon)。  
  
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
 指標[IMAGEINFO](http://msdn.microsoft.com/library/windows/desktop/bb761393)接收映像的相關資訊的結構。 此結構中的資訊可以用來直接操作影像的點陣圖。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 `IMAGEINFO`結構包含影像清單中的映像的相關資訊。  
  
##  <a name="getsafehandle"></a>CImageList::GetSafeHandle  
 呼叫此函式可擷取**m_hImageList**資料成員。  
  
```  
HIMAGELIST GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 附加的影像清單控制代碼否則**NULL**如果附加的物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&15;](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]  
  
##  <a name="m_himagelist"></a>CImageList::m_hImageList  
 附加至這個物件的影像清單控制代碼。  
  
 **HIMAGELIST m_hImageList;**  
  
### <a name="remarks"></a>備註  
 **M_hImageList**資料成員是類型的公用變數`HIMAGELIST`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&23;](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]  
  
##  <a name="operator_himagelist"></a>CImageList::operator HIMAGELIST  
 使用這個運算子來取得附加的控制代碼的`CImageList`物件。  
  
```  
operator HIMAGELIST() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，映像清單中的控制代碼所代表`CImageList`物件; 否則**NULL**。  
  
### <a name="remarks"></a>備註  
 這位操作員便轉型運算子，支援直接使用`HIMAGELIST`物件。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&16;](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]  
  
##  <a name="read"></a>CImageList::Read  
 呼叫此函式可從封存讀取影像清單。  
  
```  
BOOL Read(CArchive* pArchive);
```  
  
### <a name="parameters"></a>參數  
 `pArchive`  
 指標`CArchive`的影像清單是要讀取的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&18;](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]  
  
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
 之後的所有項目`nImage`現在下移一個位置。 例如，如果影像清單包含兩個項目，刪除第一個項目會導致其餘的項目現在是在第一個位置。 `nImage`=&0;，第一個位置中的項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&19;](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]  
  
##  <a name="replace"></a>CImageList::Replace  
 呼叫此函式可使用新的映像取代影像清單中的映像。  
  
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
 包含遮罩點陣圖指標。 如果未遮罩影像清單與使用時，會忽略此參數。  
  
 `hIcon`  
 包含點陣圖和新的映像的遮罩之圖示的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回的版本**BOOL**傳回非零值，如果成功，否則為 0。  
  
 傳回的版本`int`傳回之影像的以零為起始的索引，如果成功，否則為-1。  
  
### <a name="remarks"></a>備註  
 此成員函式呼叫之後呼叫[SetImageCount](#setimagecount)若要指派新，有效的映像以預留位置映像索引編號。  
  
### <a name="example"></a>範例  
  請參閱範例[CImageList::SetImageCount](#setimagecount)。  
  
##  <a name="setbkcolor"></a>CImageList::SetBkColor  
 呼叫此函式來設定影像清單的背景色彩。  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>參數  
 `cr`  
 若要設定背景色彩。 它可以是`CLR_NONE`。 在此情況下，映像會繪製無障礙地使用遮罩。  
  
### <a name="return-value"></a>傳回值  
 先前的背景色彩如果登錄成功。否則`CLR_NONE`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&20;](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]  
  
##  <a name="setdragcursorimage"></a>CImageList::SetDragCursorImage  
 建立新的拖曳影像合併指定的影像 （通常是滑鼠游標影像） 與目前拖曳影像。  
  
```  
BOOL SetDragCursorImage(
    int nDrag,  
    CPoint ptHotSpot);
```  
  
### <a name="parameters"></a>參數  
 *nDrag*  
 新的映像，以配合拖曳影像的索引。  
  
 `ptHotSpot`  
 新的映像中作用點的位置。  
  
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
 影像清單中指定新的映像總數值。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 如果您呼叫此成員函式，以增加影像清單中的映像數目，然後呼叫[取代](#replace)的每個額外的映像，將新的索引指派給有效的映像。 如果您無法指派至有效的映像的索引，建立新的映像的繪製作業無法預測。  
  
 如果您使用此函式來減少映像清單的大小，會釋放截斷映像。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&21;](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]  
  
##  <a name="setoverlayimage"></a>Cimagelist:: Setoverlayimage  
 呼叫此函式可用於覆疊遮罩的映像的清單中加入影像之以零為起始的索引。  
  
```  
BOOL SetOverlayImage(
    int nImage,  
    int nOverlay);
```  
  
### <a name="parameters"></a>參數  
 `nImage`  
 要使用作為覆疊遮罩的影像以零為起始的索引。  
  
 *nOverlay*  
 一個以覆疊遮罩的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 最多四個索引可以新增至清單。  
  
 覆疊遮罩是以透明方式繪製在另一個映像的映像。 使用影像繪製覆疊遮罩[cimagelist:: Draw](#draw)起始的索引，使用指定的覆疊遮罩的成員函式**INDEXTOOVERLAYMASK**巨集。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&22;](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]  
  
##  <a name="write"></a>CImageList::Write  
 呼叫此函式可寫入封存中的影像清單物件。  
  
```  
BOOL Write(CArchive* pArchive);
```  
  
### <a name="parameters"></a>參數  
 `pArchive`  
 指標`CArchive`影像清單是儲存在其中的物件。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CImageList #&17;](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CListCtrl 類別](../../mfc/reference/clistctrl-class.md)   
 [CTabCtrl 類別](../../mfc/reference/ctabctrl-class.md)

