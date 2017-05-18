---
title: "CBitmap 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- drawing, tools
- CBitmap class
- GDI bitmap
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
caps.latest.revision: 22
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ccfe592bbbae8c0eff22baa6e1baac56754ef6fc
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cbitmap-class"></a>CBitmap 類別
封裝 Windows 繪圖裝置介面 (GDI) 點陣圖，並提供操作點陣圖的成員函式。  
  
## <a name="syntax"></a>語法  
  
```  
class CBitmap : public CGdiObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CBitmap::CBitmap](#cbitmap)|建構 `CBitmap` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CBitmap::CreateBitmap](#createbitmap)|初始化具有指定的寬度、 高度和位元模式的裝置相關記憶體點陣圖物件。|  
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|初始化與點陣圖的寬度、 高度和位元模式 （如果已指定） 中指定的物件**點陣圖**結構。|  
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|初始化的點陣圖物件，使其與指定的裝置相容。|  
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|初始化具有可捨棄點陣圖與指定的裝置相容的物件。|  
|[CBitmap::FromHandle](#fromhandle)|傳回的指標`CBitmap`物件指定 windows 控制代碼時`HBITMAP`點陣圖。|  
|[CBitmap::GetBitmap](#getbitmap)|填滿**點陣圖**點陣圖的相關資訊的結構。|  
|[CBitmap::GetBitmapBits](#getbitmapbits)|將指定的點陣圖的位元複製到指定的緩衝區。|  
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|傳回點陣圖的高度與寬度。 高度和寬度會假設已設定先前[SetBitmapDimension](#setbitmapdimension)成員函式。|  
|[Cbitmap:: Loadbitmap](#loadbitmap)|藉由從應用程式的可執行檔載入一個具名的點陣圖資源，並將點陣圖附加至物件初始化的物件。|  
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|載入點陣圖，並將色彩對應至目前的系統色彩。|  
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|藉由載入預先定義的 Windows 點陣圖，並將點陣圖附加至物件初始化的物件。|  
|[CBitmap::SetBitmapBits](#setbitmapbits)|將點陣圖的位元設定為指定的位元值。|  
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|點陣圖，以 0.1 公釐為單位指定寬度和高度。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CBitmap::operator HBITMAP](#operator_hbitmap)|連接至 Windows 控制代碼傳回`CBitmap`物件。|  
  
## <a name="remarks"></a>備註  
 若要使用`CBitmap`物件，建構物件、 將點陣圖控制代碼附加至它其中一個成員函式初始化，然後呼叫物件的成員函式。  
  
 如需有關使用圖形物件，例如`CBitmap`，請參閱[圖形物件](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBitmap`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cbitmap"></a>CBitmap::CBitmap  
 建構 `CBitmap` 物件。  
  
```  
CBitmap();
```  
  
### <a name="remarks"></a>備註  
 產生的物件必須先初始化與其中一個成員函式初始化。  
  
##  <a name="createbitmap"></a>CBitmap::CreateBitmap  
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
  
 雖然無法直接顯示裝置選取點陣圖，它可以選擇作為 「 裝置內容的記憶體 」 的目前點陣圖使用[CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)並複製到任何相容的裝置內容中，使用[CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt)函式。  
  
 當您完成使用 `CBitmap` 函式所建立的 `CreateBitmap` 物件時，請先選取點陣圖並移出裝置內容，再刪除 `CBitmap` 物件。  
  
 如需詳細資訊，請參閱 **BITMAP** 結構中 **bmBits** 欄位的說明。 [點陣圖](../../mfc/reference/bitmap-structure.md)結構描述下[CBitmap::CreateBitmapIndirect](#createbitmapindirect)成員函式。  
  
##  <a name="createbitmapindirect"></a>CBitmap::CreateBitmapIndirect  
 初始化寬度、 高度和位元模式 （如果已指定） 所指向的結構中指定的點陣圖`lpBitmap`。  
  
```  
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```  
  
### <a name="parameters"></a>參數  
 `lpBitmap`  
 指向[點陣圖](../../mfc/reference/bitmap-structure.md)包含點陣圖的相關資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 雖然無法直接顯示裝置選取點陣圖，它可以選擇作為記憶體裝置內容的目前點陣圖使用[CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)並複製到任何相容的裝置內容中，使用[CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt)或[CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)函式。 ( [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt)函式可以將目前的筆刷的點陣圖複製到顯示裝置內容的直接。)  
  
 如果**點陣圖**指向結構`lpBitmap`參數已使用滿`GetObject`函式，未指定點陣圖的位元的點陣圖未初始化。 若要初始化點陣圖，應用程式可以使用函式例如[CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt)或[SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973)位元複製的第一個參數所識別的點陣圖`CGdiObject::GetObject`為所建立的點陣圖`CreateBitmapIndirect`。  
  
 當您完成使用`CBitmap`物件以建立`CreateBitmapIndirect`函式，先選取 從裝置內容中，點陣圖，然後刪除`CBitmap`物件。  
  
##  <a name="createcompatiblebitmap"></a>CBitmap::CreateCompatibleBitmap  
 初始化與所指定的裝置相容的點陣圖`pDC`。  
  
```  
BOOL CreateCompatibleBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 指定裝置內容。  
  
 `nWidth`  
 指定點陣圖的寬度 (以像素為單位)。  
  
 `nHeight`  
 指定點陣圖的高度 (以像素為單位)。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 點陣圖的色彩平面的數目或指定的裝置內容的每個像素的位元格式相同。 與指定的任何記憶體裝置的目前點陣圖當做`pDC`。  
  
 如果`pDC`是記憶體裝置內容，傳回的點陣圖的裝置內容中具有相同的格式，為目前選取的點陣圖。 「 裝置內容的記憶體 」 是記憶體的表示顯示介面區塊。 它可以用來準備在記憶體中的映像之前將它們複製到相容的裝置的實際顯示表面。  
  
 建立記憶體裝置內容時，GDI 會自動為其選取股票的單色點陣圖。  
  
 由於色彩記憶體裝置內容中可能有色彩或選取的單色點陣圖，所傳回的點陣圖格式`CreateCompatibleBitmap`函式不一定相同; 不過，相容 nonmemory 裝置內容的點陣圖格式一律為裝置的格式。  
  
 當您完成使用`CBitmap`物件以建立`CreateCompatibleBitmap`函式，先選取 從裝置內容中，點陣圖，然後刪除`CBitmap`物件。  
  
##  <a name="creatediscardablebitmap"></a>CBitmap::CreateDiscardableBitmap  
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
 指定點陣圖的寬度 （以位元）。  
  
 `nHeight`  
 指定的點陣圖的高度 （以位元為單位）。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 點陣圖的色彩平面的數目或指定的裝置內容的每個像素的位元格式相同。 應用程式可以選取這個點陣圖做為與指定的記憶體裝置的目前點陣圖`pDC`。  
  
 Windows 可以捨棄只有在應用程式尚未選取顯示內容，這個函式所建立的點陣圖。 如果未選取，並加以選取，嘗試更新版本的應用程式時，Windows 會捨棄點陣圖[CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)函式會傳回**NULL**。  
  
 當您完成使用`CBitmap`物件以建立`CreateDiscardableBitmap`函式，先選取 從裝置內容中，點陣圖，然後刪除`CBitmap`物件。  
  
##  <a name="fromhandle"></a>CBitmap::FromHandle  
 若要將指標傳回`CBitmap`物件指定 Windows GDI 點陣圖控制代碼時。  
  
```  
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>參數  
 `hBitmap`  
 指定 Windows GDI 點陣圖。  
  
### <a name="return-value"></a>傳回值  
 指標`CBitmap`物件如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果`CBitmap`物件尚未附加至控制代碼，暫存`CBitmap`會建立並附加物件。 此暫存`CBitmap`僅直到下一次應用程式在其事件迴圈中有閒置時間，在這次所有暫存圖形會刪除物件，物件才有效。 另一種說法是，此暫存物件的一個視窗訊息處理期間才有效。  
  
##  <a name="getbitmap"></a>CBitmap::GetBitmap  
 擷取附加點陣圖影像屬性。  
  
```  
int GetBitmap(BITMAP* pBitMap);
```  
  
### <a name="parameters"></a>參數  
 `pBitMap`  
 指標[點陣圖結構](../../mfc/reference/bitmap-structure.md)結構，將會收到映像內容。 此參數不得為 `NULL`。  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="getbitmapbits"></a>CBitmap::GetBitmapBits  
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
 如果此方法成功，複製到緩衝區的位元組數目否則為 0。  
  
### <a name="remarks"></a>備註  
 使用[CBitmap::GetBitmap](#getbitmap)來判斷所需的緩衝區大小。  
  
##  <a name="getbitmapdimension"></a>CBitmap::GetBitmapDimension  
 傳回點陣圖的高度與寬度。  
  
```  
CSize GetBitmapDimension() const;  
```  
  
### <a name="return-value"></a>傳回值  
 點陣圖的高度與寬度以 0.1 公釐為單位。 高度處於**cy**成員`CSize`物件和寬度都在**cx**成員。 如果點陣圖的寬度和高度尚未設定使用`SetBitmapDimension`，傳回值為 0。  
  
### <a name="remarks"></a>備註  
 高度和寬度會假設已使用先前設定[SetBitmapDimension](#setbitmapdimension)成員函式。  
  
##  <a name="loadbitmap"></a>Cbitmap:: Loadbitmap  
 載入所命名的點陣圖資源`lpszResourceName`中的 ID 編號來識別或`nIDResource`從應用程式的可執行檔。  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>參數  
 `lpszResourceName`  
 指向以 null 結束的字串，其中包含點陣圖資源的名稱。  
  
 `nIDResource`  
 指定點陣圖資源的資源 ID 編號。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 載入的點陣圖會附加至`CBitmap`物件。  
  
 如果點陣圖由`lpszResourceName`不存在，或沒有記憶體不足，無法載入點陣圖，函式會傳回 0。  
  
 您可以使用[CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)函式來刪除點陣圖載入`LoadBitmap`函式，或`CBitmap`解構函式會為您刪除物件。  
  
> [!CAUTION]
>  刪除物件之前，請確定未選取放入裝置內容。  
  
 3.1 和更新版本的 Windows 版本，已加入下列點陣圖︰  
  
 **OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI**  
  
 這些點陣圖找不到的 Windows 版本的裝置驅動程式 3.0 版及更早版本。 點陣圖，以及其外觀的完整清單，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="loadmappedbitmap"></a>CBitmap::LoadMappedBitmap  
 呼叫此成員函式可載入點陣圖，並將色彩對應至目前的系統色彩。  
  
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
 所指的色彩對應數目`lpColorMap`。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 根據預設，`LoadMappedBitmap`將對應常用於按鈕圖像 （glyph） 的色彩。  
  
 如需建立對應的點陣圖的資訊，請參閱 Windows 函式[CreateMappedBitmap](http://go.microsoft.com/fwlink/linkid=230562)和[COLORMAP](http://msdn.microsoft.com/library/windows/desktop/bb760448)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="loadoembitmap"></a>CBitmap::LoadOEMBitmap  
 載入 Windows 所使用的預先定義的點陣圖。  
  
```  
BOOL LoadOEMBitmap(UINT nIDBitmap);
```  
  
### <a name="parameters"></a>參數  
 `nIDBitmap`  
 預先定義的 Windows 點陣圖的 ID 編號。 可能的值如下所示的視窗。H:  
  
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
 點陣圖名稱開頭**OBM_OLD**代表 3.0 以前的 Windows 版本中所使用的點陣圖。  
  
 請注意，常數**OEMRESOURCE**必須包含 WINDOWS 前先定義。若要使用的任何 H **OBM_**常數。  
  
##  <a name="operator_hbitmap"></a>CBitmap::operator HBITMAP  
 使用這個運算子來取得附加的 Windows GDI 控制代碼的`CBitmap`物件。  
  
```  
operator HBITMAP() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，Windows GDI 物件的控制代碼所代表`CBitmap`物件; 否則**NULL**。  
  
### <a name="remarks"></a>備註  
 這位操作員便轉型運算子，支援直接使用`HBITMAP`物件。  
  
 如需使用圖形物件的詳細資訊，請參閱[圖形物件](http://msdn.microsoft.com/library/windows/desktop/dd144962)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setbitmapbits"></a>CBitmap::SetBitmapBits  
 將點陣圖的位元設定為所指定的位元值`lpBits`。  
  
```  
DWORD SetBitmapBits(
    DWORD dwCount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>參數  
 `dwCount`  
 指定所指向的位元組數目`lpBits`。  
  
 `lpBits`  
 指向**位元組**陣列，其中包含要複製到的像素值`CBitmap`物件。 為了要能夠正確地呈現其影像的點陣圖，值應格式化為符合 CBitmap 執行個體建立時所指定的高度、 寬度和色彩深度值。 如需詳細資訊，請參閱[CBitmap::CreateBitmap](#createbitmap)。  
  
### <a name="return-value"></a>傳回值  
 點陣圖位元; 設定中使用的位元組數目0，表示函式失敗。  
  
##  <a name="setbitmapdimension"></a>CBitmap::SetBitmapDimension  
 點陣圖，以 0.1 公釐為單位指定寬度和高度。  
  
```  
CSize SetBitmapDimension(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>參數  
 `nWidth`  
 指定的寬度 （以 0.1 公釐為單位） 的點陣圖。  
  
 `nHeight`  
 指定的高度 （以 0.1 公釐為單位） 的點陣圖。  
  
### <a name="return-value"></a>傳回值  
 上一個點陣圖的尺寸。 高度處於**cy**成員變數`CSize`物件和寬度都在**cx**成員變數。  
  
### <a name="remarks"></a>備註  
 GDI 不會使用這些值來傳回這些應用程式呼叫時，除了[GetBitmapDimension](#getbitmapdimension)成員函式。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 MDI](../../visual-cpp-samples.md)   
 [CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)


