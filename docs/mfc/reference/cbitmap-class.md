---
title: CBitmap 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
dev_langs:
- C++
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5b931c7ad4b560ce247f78dcb126f9669bceb67
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355859"
---
# <a name="cbitmap-class"></a>CBitmap 類別
封裝 Windows 繪圖裝置介面 (GDI) 點陣圖，並提供操作點陣圖的成員函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CBitmap : public CGdiObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CBitmap::CBitmap](#cbitmap)|建構 `CBitmap` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CBitmap::CreateBitmap](#createbitmap)|初始化具有指定的寬度、 高度和位元模式的裝置而異的記憶體點陣圖的物件。|  
|[Bitmap](#createbitmapindirect)|初始化物件的點陣圖寬度、 高度和位元模式 （如果已指定） 中指定**點陣圖**結構。|  
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|初始化與點陣圖物件，使其與指定的裝置相容。|  
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|初始化具有可捨棄點陣圖與指定的裝置相容的物件。|  
|[CBitmap::FromHandle](#fromhandle)|將指標傳回至`CBitmap`物件時指定的 windows 控制代碼`HBITMAP`點陣圖。|  
|[CBitmap::GetBitmap](#getbitmap)|填滿**點陣圖**點陣圖的相關資訊的結構。|  
|[CBitmap::GetBitmapBits](#getbitmapbits)|將指定的點陣圖的位元複製到指定的緩衝區。|  
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|傳回點陣圖的高度與寬度。 高度和寬度會假設已設定先前[SetBitmapDimension](#setbitmapdimension)成員函式。|  
|[Cbitmap:: Loadbitmap](#loadbitmap)|從應用程式的可執行檔載入具名的點陣圖資源，並將點陣圖附加到物件來初始化物件。|  
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|載入點陣圖，並將對應至目前的系統色彩的色彩。|  
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|載入預先定義的 Windows 點陣圖，並將點陣圖附加到物件來初始化物件。|  
|[CBitmap::SetBitmapBits](#setbitmapbits)|將點陣圖的位元設定為指定的位元值。|  
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|會指派寬度和高度，以 0.1 公釐為單位的點陣圖。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[HBITMAP CBitmap::operator](#operator_hbitmap)|傳回附加至的 Windows 控制代碼`CBitmap`物件。|  
  
## <a name="remarks"></a>備註  
 若要使用`CBitmap`物件、 建構物件，將點陣圖的控制代碼附加至使用下列其中一個初始化成員函式，並再呼叫物件的成員函式。  
  
 如需有關使用圖形物件，例如`CBitmap`，請參閱[圖形物件](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBitmap`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cbitmap"></a>  CBitmap::CBitmap  
 建構 `CBitmap` 物件。  
  
```  
CBitmap();
```  
  
### <a name="remarks"></a>備註  
 產生的物件必須初始化以初始化成員函式的其中一個。  
  
##  <a name="createbitmap"></a>  CBitmap::CreateBitmap  
 初始化具有指定寬度、高度和位元模式之因裝置而異的記憶體點陣圖。  
  
```  
BOOL CreateBitmap(
    int nWidth,  
    int nHeight,  
    UINT nPlanes,  
    UINT nBitcount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>參數  
 `nWidth`  
 指定點陣圖的寬度 (以像素為單位)。  
  
 `nHeight`  
 指定點陣圖的高度 (以像素為單位)。  
  
 `nPlanes`  
 指定點陣圖中色彩平面的數目。  
  
 `nBitcount`  
 指定每個顯示像素的色彩位元數目。  
  
 `lpBits`  
 指向位元組陣列，其中包含初始點陣圖位元值。 如果為 **NULL**，則不會初始化新的點陣圖。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 若是彩色點陣圖， `nPlanes` 或 `nBitcount` 參數應設為 1。 如果這兩個參數都設為 1， `CreateBitmap` 會建立單色點陣圖。  
  
 雖然無法直接選取點陣圖，顯示裝置，也可以選取作為 「 記憶體裝置內容 」 的目前點陣圖使用[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)並複製到任何相容的裝置內容中，使用[Cdc:: bitblt](../../mfc/reference/cdc-class.md#bitblt)函式。  
  
 當您完成使用 `CBitmap` 函式所建立的 `CreateBitmap` 物件時，請先選取點陣圖並移出裝置內容，再刪除 `CBitmap` 物件。  
  
 如需詳細資訊，請參閱 **BITMAP** 結構中 **bmBits** 欄位的說明。 [點陣圖](../../mfc/reference/bitmap-structure.md)結構中所述[Bitmap](#createbitmapindirect)成員函式。  
  
##  <a name="createbitmapindirect"></a>  Bitmap  
 初始化具有寬度、 高度和位元模式 （如果已指定） 所指向的結構中指定的點陣圖`lpBitmap`。  
  
```  
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```  
  
### <a name="parameters"></a>參數  
 `lpBitmap`  
 指向[點陣圖](../../mfc/reference/bitmap-structure.md)包含點陣圖的相關資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 雖然無法直接選取點陣圖，顯示裝置，也可以選取做為記憶體裝置內容的目前點陣圖使用[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)並複製到任何相容的裝置內容中，使用[Cdc:: bitblt](../../mfc/reference/cdc-class.md#bitblt)或[CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)函式。 ( [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt)函式可以將目前的筆刷的點陣圖複製直接到顯示裝置內容。)  
  
 如果**點陣圖**結構所指`lpBitmap`使用參數填入`GetObject`函式未指定點陣圖的位元和點陣圖未初始化。 若要初始化點陣圖，應用程式可以使用函式例如[cdc:: bitblt](../../mfc/reference/cdc-class.md#bitblt)或[SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973)位元複製的第一個參數所識別的點陣圖`CGdiObject::GetObject`為所建立的點陣圖`CreateBitmapIndirect`.  
  
 當您完成使用`CBitmap`物件以建立`CreateBitmapIndirect`函式，請先選取點陣圖並移出裝置內容，然後刪除`CBitmap`物件。  
  
##  <a name="createcompatiblebitmap"></a>  CBitmap::CreateCompatibleBitmap  
 初始化與所指定的裝置相容的點陣圖`pDC`。  
  
```  
BOOL CreateCompatibleBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指定的裝置內容。  
  
 `nWidth`  
 指定點陣圖的寬度 (以像素為單位)。  
  
 `nHeight`  
 指定點陣圖的高度 (以像素為單位)。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 點陣圖會具有相同色彩平面的數目或指定的裝置內容相同的每個像素的位元格式。 當做與所指定相容的任何記憶體裝置的目前點陣圖`pDC`。  
  
 如果`pDC`是記憶體裝置內容，傳回的點陣圖中的裝置內容具有相同的格式，為目前選取的點陣圖。 「 記憶體裝置內容 」 是記憶體的表示顯示介面區塊。 它可以用來準備在記憶體中的映像，然後再將它們複製到相容的裝置的實際顯示介面。  
  
 建立記憶體裝置內容時，GDI 會自動為它選取內建的單色點陣圖。  
  
 由於色彩記憶體裝置內容中可以有色彩或選取的單色點陣圖，所傳回的點陣圖格式`CreateCompatibleBitmap`函式不一定是相同的; 不過，會一律在相容 nonmemory 裝置內容的點陣圖格式裝置的格式。  
  
 當您完成使用`CBitmap`物件以建立`CreateCompatibleBitmap`函式，請先選取點陣圖並移出裝置內容，然後刪除`CBitmap`物件。  
  
##  <a name="creatediscardablebitmap"></a>  CBitmap::CreateDiscardableBitmap  
 初始化與所識別的裝置內容的可捨棄點陣圖`pDC`。  
  
```  
BOOL CreateDiscardableBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指定裝置內容。  
  
 `nWidth`  
 指定點陣圖的寬度 （以位元為單位）。  
  
 `nHeight`  
 指定點陣圖的高度 （以位元為單位）。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 點陣圖會具有相同色彩平面的數目或指定的裝置內容相同的每個像素的位元格式。 應用程式可以做為與所指定的記憶體裝置的目前點陣圖選取此點陣圖`pDC`。  
  
 Windows 可以捨棄應用程式尚未選取顯示內容時，只有這個函式所建立的點陣圖。 如果未選取，並加以選取，嘗試更新版本的應用程式時，Windows 會捨棄點陣圖[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)函式會傳回**NULL**。  
  
 當您完成使用`CBitmap`物件以建立`CreateDiscardableBitmap`函式，請先選取點陣圖並移出裝置內容，然後刪除`CBitmap`物件。  
  
##  <a name="fromhandle"></a>  CBitmap::FromHandle  
 將指標傳回至`CBitmap`物件時指定 Windows GDI 點陣圖的控制代碼。  
  
```  
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>參數  
 `hBitmap`  
 指定 Windows GDI 點陣圖。  
  
### <a name="return-value"></a>傳回值  
 指標`CBitmap`物件，如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果`CBitmap`物件未附加至控制代碼，暫存`CBitmap`物件會建立並附加。 此暫存`CBitmap`僅直到下一次應用程式有其事件迴圈中的閒置時間，在這次所有暫存圖形已刪除物件，物件才有效。 另一種說法是，暫存物件的一個視窗訊息處理期間才有效。  
  
##  <a name="getbitmap"></a>  CBitmap::GetBitmap  
 擷取映像屬性為附加的點陣圖。  
  
```  
int GetBitmap(BITMAP* pBitMap);
```  
  
### <a name="parameters"></a>參數  
 `pBitMap`  
 指標[點陣圖結構](../../mfc/reference/bitmap-structure.md)將會收到在映像內容的結構。 此參數不得為 `NULL`。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果該方法成功。否則便是 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getbitmapbits"></a>  CBitmap::GetBitmapBits  
 將附加的點陣圖的位元模式複製到指定的緩衝區。  
  
```  
DWORD GetBitmapBits(
    DWORD dwCount,  
    LPVOID lpBits) const;  
```  
  
### <a name="parameters"></a>參數  
 `dwCount`  
 要複製到緩衝區的位元組數目。  
  
 `lpBits`  
 將會收到點陣圖的緩衝區指標。  
  
### <a name="return-value"></a>傳回值  
 如果該方法成功; 複製到緩衝區的位元組數目否則便是 0。  
  
### <a name="remarks"></a>備註  
 使用[CBitmap::GetBitmap](#getbitmap)來決定所需的緩衝區大小。  
  
##  <a name="getbitmapdimension"></a>  CBitmap::GetBitmapDimension  
 傳回點陣圖的高度與寬度。  
  
```  
CSize GetBitmapDimension() const;  
```  
  
### <a name="return-value"></a>傳回值  
 點陣圖的高度與寬度以 0.1 公釐為單位。 高度處於**cy**隸屬`CSize`物件和寬度都在**cx**成員。 如果點陣圖的寬度和高度尚未設定使用`SetBitmapDimension`，傳回值是 0。  
  
### <a name="remarks"></a>備註  
 高度和寬度會假設已使用先前設定[SetBitmapDimension](#setbitmapdimension)成員函式。  
  
##  <a name="loadbitmap"></a>  Cbitmap:: Loadbitmap  
 載入所命名的點陣圖資源`lpszResourceName`或中的 ID 編號識別`nIDResource`從應用程式的可執行檔。  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>參數  
 `lpszResourceName`  
 指向以 null 終止的字串，包含點陣圖資源的名稱。  
  
 `nIDResource`  
 指定點陣圖資源的資源識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 載入的點陣圖附加至`CBitmap`物件。  
  
 如果所識別的點陣圖`lpszResourceName`不存在或如果沒有記憶體不足，無法載入點陣圖，函數會傳回 0。  
  
 您可以使用[CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)所載入的函式來刪除點陣圖`LoadBitmap`函式，或`CBitmap`解構函式會為您刪除物件。  
  
> [!CAUTION]
>  刪除物件之前，請確定未選取放入裝置內容中。  
  
 3.1 和更新版本的 Windows 版本已新增下列點陣圖：  
  
 **OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI**  
  
 這些點陣圖找不到的 Windows 版本的裝置驅動程式 3.0 版及更早版本。 點陣圖，以及其外觀的完整清單，請參閱 Windows SDK。  
  
##  <a name="loadmappedbitmap"></a>  CBitmap::LoadMappedBitmap  
 呼叫此成員函式可載入點陣圖並對應至目前的系統色彩的色彩。  
  
```  
BOOL LoadMappedBitmap(
    UINT nIDBitmap,  
    UINT nFlags = 0,  
    LPCOLORMAP lpColorMap = NULL,  
    int nMapSize = 0);
```  
  
### <a name="parameters"></a>參數  
 `nIDBitmap`  
 點陣圖資源的識別碼。  
  
 `nFlags`  
 點陣圖的旗標。 可以是零或**CMB_MASKED**。  
  
 `lpColorMap`  
 指標**COLORMAP**結構，其中包含對應的點陣圖所需的色彩資訊。 如果這個參數是**NULL**，此函數會使用預設的色彩對應。  
  
 *nMapSize*  
 色彩對應的數字所指`lpColorMap`。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 根據預設，`LoadMappedBitmap`將對應常用於按鈕字符的色彩。  
  
 如需建立對應的點陣圖的資訊，請參閱 Windows 函式[CreateMappedBitmap](http://go.microsoft.com/fwlink/p/?linkid=230562)和[COLORMAP](http://msdn.microsoft.com/library/windows/desktop/bb760448) Windows SDK 中的結構。  
  
##  <a name="loadoembitmap"></a>  CBitmap::LoadOEMBitmap  
 載入 Windows 所使用的預先定義的點陣圖。  
  
```  
BOOL LoadOEMBitmap(UINT nIDBitmap);
```  
  
### <a name="parameters"></a>參數  
 `nIDBitmap`  
 預先定義的 Windows 點陣圖的 ID 編號。 可能的值如下所示從 WINDOWS。H:  
  
|||  
|-|-|  
|**OBM_BTNCORNERS**|**OBM_OLD_RESTORE**|  
|**OBM_BTSIZE**|**OBM_OLD_RGARROW**|  
|**OBM_CHECK**|**OBM_OLD_UPARROW**|  
|**OBM_CHECKBOXES**|**OBM_OLD_ZOOM**|  
|**OBM_CLOSE**|**OBM_REDUCE**|  
|**OBM_COMBO**|**OBM_REDUCED**|  
|**OBM_DNARROW**|**OBM_RESTORE**|  
|**OBM_DNARROWD**|**OBM_RESTORED**|  
|**OBM_DNARROWI**|**OBM_RGARROW**|  
|**OBM_LFARROW**|**OBM_RGARROWD**|  
|**OBM_LFARROWD**|**OBM_RGARROWI**|  
|**OBM_LFARROWI**|**OBM_SIZE**|  
|**OBM_MNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_CLOSE**|**OBM_UPARROWD**|  
|**OBM_OLD_DNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_LFARROW**|**OBM_ZOOM**|  
|**OBM_OLD_REDUCE**|**OBM_ZOOMD**|  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 點陣圖名稱開頭**OBM_OLD**代表 3.0 之前的 Windows 版本中所使用的點陣圖。  
  
 請注意，常數**OEMRESOURCE**包含 WINDOWS 之前，必須定義。若要使用的任何 H **OBM_** 常數。  
  
##  <a name="operator_hbitmap"></a>  HBITMAP CBitmap::operator  
 使用此運算子，以取得附加的 Windows GDI 控制代碼的`CBitmap`物件。  
  
```  
operator HBITMAP() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，Windows GDI 物件的控制代碼來表示`CBitmap`物件; 否則**NULL**。  
  
### <a name="remarks"></a>備註  
 這位操作員便轉型運算子，可支援直接使用`HBITMAP`物件。  
  
 如需有關使用圖形物件的詳細資訊，請參閱[圖形物件](http://msdn.microsoft.com/library/windows/desktop/dd144962)Windows SDK 中。  
  
##  <a name="setbitmapbits"></a>  CBitmap::SetBitmapBits  
 設定所指定的位元值的位元點陣圖`lpBits`。  
  
```  
DWORD SetBitmapBits(
    DWORD dwCount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>參數  
 `dwCount`  
 指定所指向的位元組數目`lpBits`。  
  
 `lpBits`  
 指向**位元組**陣列，其中包含要複製到其中的像素值`CBitmap`物件。 為了要能夠正確地呈現其影像點陣圖，值應格式化為符合 CBitmap 執行個體已建立時所指定的高度、 寬度和色彩深度值。 如需詳細資訊，請參閱[CBitmap::CreateBitmap](#createbitmap)。  
  
### <a name="return-value"></a>傳回值  
 點陣圖位元; 設定中使用的位元組數目0，表示函式失敗。  
  
##  <a name="setbitmapdimension"></a>  CBitmap::SetBitmapDimension  
 會指派寬度和高度，以 0.1 公釐為單位的點陣圖。  
  
```  
CSize SetBitmapDimension(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>參數  
 `nWidth`  
 指定的寬度 （以 0.1 公釐為單位） 的點陣圖。  
  
 `nHeight`  
 指定的高度 （單位 0.1 公釐） 的點陣圖。  
  
### <a name="return-value"></a>傳回值  
 先前的點陣圖維度。 高度處於**cy**成員變數`CSize`物件和寬度都在**cx**成員變數。  
  
### <a name="remarks"></a>備註  
 GDI 不會使用這些值除了到它們時傳回應用程式呼叫[GetBitmapDimension](#getbitmapdimension)成員函式。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDI](../../visual-cpp-samples.md)   
 [CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)

