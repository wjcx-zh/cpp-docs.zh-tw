---
title: "CBrush 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
dev_langs:
- C++
helpviewer_keywords:
- brushes, CBrush class
- CBrush class
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
caps.latest.revision: 21
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
ms.openlocfilehash: efcbe2757de3a7e4621e2b20c88726ead111cf8c
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cbrush-class"></a>CBrush 類別
封裝 Windows 繪圖裝置介面 (GDI) 筆刷。  
  
## <a name="syntax"></a>語法  
  
```  
class CBrush : public CGdiObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CBrush::CBrush](#cbrush)|建構 `CBrush` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CBrush::CreateBrushIndirect](#createbrushindirect)|初始化與樣式、 色彩和模式中指定的筆刷[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)結構。|  
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|與裝置無關點陣圖 (DIB) 所指定的模式，初始化筆刷。|  
|[CBrush::CreateHatchBrush](#createhatchbrush)|初始化具有指定陰影的模式和色彩的筆刷。|  
|[CBrush::CreatePatternBrush](#createpatternbrush)|指定點陣圖的模式，初始化筆刷。|  
|[CBrush::CreateSolidBrush](#createsolidbrush)|初始化具有指定的單色筆刷。|  
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|建立為預設系統色彩的筆刷。|  
|[CBrush::FromHandle](#fromhandle)|傳回的指標`CBrush`物件指定 windows 控制代碼時`HBRUSH`物件。|  
|[CBrush::GetLogBrush](#getlogbrush)|取得[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)結構。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CBrush::operator HBRUSH](#operator_hbrush)|連接至 Windows 控制代碼傳回`CBrush`物件。|  
  
## <a name="remarks"></a>備註  
 若要使用`CBrush`物件，建構`CBrush`物件，並將它傳遞到任何`CDC`需要筆刷的成員函式。  
  
 可以實線、 筆刷，影線，或圖樣。  
  
 如需有關`CBrush`，請參閱[圖形物件](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBrush`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cbrush"></a>CBrush::CBrush  
 建構 `CBrush` 物件。  
  
```  
CBrush(); 
CBrush(COLORREF crColor); 
CBrush(int nIndex, COLORREF crColor); 
explicit CBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>參數  
 `crColor`  
 指定做為 RGB 色彩的筆刷的前景色彩。 如果影線筆刷，此參數會指定影線色彩。  
  
 `nIndex`  
 指定的影線類型的筆刷。 它可以是下列值之一︰  
  
- `HS_BDIAGONAL`在 45 度向下串聯 （由左到右）  
  
- `HS_CROSS`水平和垂直有斜紋  
  
- `HS_DIAGCROSS`Crosshatch 45 度角  
  
- `HS_FDIAGONAL`在 45 度向上串聯 （由左到右）  
  
- `HS_HORIZONTAL`水平影線  
  
- `HS_VERTICAL`垂直規劃  
  
 `pBitmap`  
 指向`CBitmap`物件，指定與筆刷繪製的點陣圖。  
  
### <a name="remarks"></a>備註  
 `CBrush`有四個多載的建構函式。不使用引數的建構函式建構未初始化`CBrush`物件，必須先初始化之後才能使用。  
  
 如果您使用不含引數的建構函式，您必須先初始化所產生的`CBrush`物件[createsolidbrush 以](#createsolidbrush)， [CreateHatchBrush](#createhatchbrush)， [CreateBrushIndirect](#createbrushindirect)， [CreatePatternBrush](#createpatternbrush)，或[CreateDIBPatternBrush](#createdibpatternbrush)。 如果您使用其中一個引數的建構函式，然後再初始化是必要。 如果發生錯誤，而不使用引數的建構函式一定會成功，則引數的建構函式可以擲回例外狀況。  
  
 第一個建構函式[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)參數建構實心筆刷使用指定的色彩。 指定 RGB 值的色彩，以及可以使用建構`RGB`WINDOWS 中的巨集。H.  
  
 具有兩個參數的建構函式建構規劃筆刷。 `nIndex`參數指定的索引影線圖樣。 `crColor`參數指定的色彩。  
  
 建構函式`CBitmap`參數建構圖樣筆刷。 參數會識別點陣圖。 點陣圖會假設已經建立使用[CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)， [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)， [cbitmap:: Loadbitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)，或[CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)。 點陣圖，填滿模式中使用的最小大小為 8 個像素 8 個像素。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&21;](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]  
  
##  <a name="createbrushindirect"></a>CBrush::CreateBrushIndirect  
 初始化與樣式、 色彩和模式中指定的筆刷[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)結構。  
  
```  
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```  
  
### <a name="parameters"></a>參數  
 *lpLogBrush*  
 指向[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)包含筆刷的相關資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 接著為目前的筆刷，適用於任何裝置的內容選取筆刷。  
  
 使用目前的文字和背景色彩繪製使用 1 平面 （每像素的 1 位元） 的單色點陣圖建立筆刷。 使用目前的文字色彩來繪製像素為單位，由位元設為 0。 使用目前的背景色彩來繪製像素為單位，由位元設為 1。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&22;](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]  
  
##  <a name="createdibpatternbrush"></a>CBrush::CreateDIBPatternBrush  
 與裝置無關點陣圖 (DIB) 所指定的模式，初始化筆刷。  
  
```  
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,  
    UINT nUsage);

 
BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,  
    UINT nUsage);
```  
  
### <a name="parameters"></a>參數  
 *hPackedDIB*  
 識別包含封裝的與裝置無關點陣圖 (DIB) 的全域記憶體物件。  
  
 *nUsage*  
 指定是否**bmiColors []**欄位[BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md)資料結構 （「 封裝 DIB 」 的一部分） 中包含明確的 RGB 值或索引目前實現邏輯調色盤。 參數必須是下列值之一︰  
  
- **DIB_PAL_COLORS**色彩表包含 16 位元索引的陣列。  
  
- **DIB_RGB_COLORS**色彩表包含常值的 RGB 值。  
  
 *lpPackedDIB*  
 指向包含壓縮 DIB`BITMAPINFO`後面緊跟著定義點陣圖的像素的位元組陣列的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 接著選取筆刷為任何支援點陣作業的裝置內容。  
  
 處理 DIB 的方式，不同的兩個版本︰  
  
-   在第一個版本中，若要取得的控制代碼 DIB 您呼叫 Windows **GlobalAlloc**函式來配置全域記憶體區塊，並使用壓縮 DIB，然後填滿記憶體。  
  
-   在第二個版本，就不需要呼叫**GlobalAlloc**壓縮 DIB 配置記憶體。  
  
 壓縮的 DIB 組成`BITMAPINFO`後面緊跟著定義點陣圖的像素的位元組陣列的資料結構。 點陣圖做為填滿模式應該是 8 個像素 8 個像素。 如果點陣圖較大，Windows 會建立填滿模式中使用對應的前 8 的資料列和 8 個資料行的點陣圖左上角像素的位元。  
  
 當應用程式放入單色裝置內容中，選取兩個色彩 DIB 圖樣筆刷時，Windows 會忽略 DIB 內指定的色彩，並改為顯示使用的裝置內容的文字和背景色彩的圖樣筆刷。 使用文字的色彩來顯示對應到 DIB （位於 DIB 色彩表中的位移 0） 的第一個色彩的像素為單位。 使用背景色彩來顯示對應到 （位移 1 色彩表中） 的第二個色彩的像素為單位。  
  
 使用下列 Windows 功能的相關資訊，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]:  
  
- [CreateDIBPatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183492) (僅為針對 3.0 之前的 Windows 版本所撰寫的應用程式相容性提供此函式; 使用**CreateDIBPatternBrushPt**函式。)  
  
- [CreateDIBPatternBrushPt](http://msdn.microsoft.com/library/windows/desktop/dd183493) （適用於 Win32 應用程式應該使用此函式）。  
  
- [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&23;](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]  
  
##  <a name="createhatchbrush"></a>CBrush::CreateHatchBrush  
 初始化具有指定陰影的模式和色彩的筆刷。  
  
```  
BOOL CreateHatchBrush(
    int nIndex,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定的影線類型的筆刷。 它可以是下列值之一︰  
  
- `HS_BDIAGONAL`在 45 度向下串聯 （由左到右）  
  
- `HS_CROSS`水平和垂直有斜紋  
  
- `HS_DIAGCROSS`Crosshatch 45 度角  
  
- `HS_FDIAGONAL`在 45 度向上串聯 （由左到右）  
  
- `HS_HORIZONTAL`水平影線  
  
- `HS_VERTICAL`垂直規劃  
  
 `crColor`  
 指定前景色彩的筆刷做為 RGB 色彩 （影線色彩）。 請參閱[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 接著為目前的筆刷，適用於任何裝置的內容選取筆刷。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&24;](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]  
  
##  <a name="createpatternbrush"></a>CBrush::CreatePatternBrush  
 指定點陣圖的模式，初始化筆刷。  
  
```  
BOOL CreatePatternBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>參數  
 `pBitmap`  
 識別點陣圖。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 接著選取筆刷為任何支援點陣作業的裝置內容。 所識別的點陣圖`pBitmap`通常會使用初始化[CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)， [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)， [cbitmap:: Loadbitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)，或[CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)函式。  
  
 點陣圖做為填滿模式應該是 8 個像素 8 個像素。 如果點陣圖是較大，Windows 只會使用對應前 8 個資料列和資料行的點陣圖左上角像素的位元。  
  
 可以刪除圖樣筆刷，而不會影響相關聯的點陣圖。 這表示點陣圖可以用來建立任意數目的圖樣筆刷。  
  
 使用目前的文字和背景色彩繪製使用 （1 色彩平面上，每個像素的 1 位元） 的單色點陣圖建立筆刷。 使用目前的文字色彩繪製像素為單位，由位元設為 0。 使用目前的背景色彩繪製像素為單位，由位元設為 1。  
  
 如需使用[CreatePatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183508)，Windows 函式，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&25;](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]  
  
##  <a name="createsolidbrush"></a>CBrush::CreateSolidBrush  
 初始化具有指定的單色筆刷。  
  
```  
BOOL CreateSolidBrush(COLORREF crColor);
```  
  
### <a name="parameters"></a>參數  
 `crColor`  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)結構，指定的筆刷色彩。 指定 RGB 值的色彩，以及可以使用建構`RGB`WINDOWS 中的巨集。H.  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 接著為目前的筆刷，適用於任何裝置的內容選取筆刷。  
  
 當應用程式已完成使用所建立的筆刷`CreateSolidBrush`，它應該選取從裝置內容的筆刷。  
  
### <a name="example"></a>範例  
  請參閱範例[CBrush::CBrush](#cbrush)。  
  
##  <a name="createsyscolorbrush"></a>CBrush::CreateSysColorBrush  
 初始化筆刷色彩。  
  
```  
BOOL CreateSysColorBrush(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定的色彩索引。 這個值對應於用來繪製一個 21 視窗元素的色彩。 請參閱[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]值的清單。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 接著為目前的筆刷，適用於任何裝置的內容選取筆刷。  
  
 當應用程式已完成使用所建立的筆刷`CreateSysColorBrush`，它應該選取從裝置內容的筆刷。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&26;](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]  
  
##  <a name="fromhandle"></a>CBrush::FromHandle  
 傳回的指標`CBrush`物件指定 windows 控制代碼時[HBRUSH](#operator_hbrush)物件。  
  
```  
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```  
  
### <a name="parameters"></a>參數  
 `hBrush`  
 `HANDLE`為 Windows GDI 筆刷。  
  
### <a name="return-value"></a>傳回值  
 指標`CBrush`物件如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果`CBrush`物件尚未附加至控制代碼，暫存`CBrush`會建立並附加物件。 此暫存`CBrush`物件是否有效，只會等到下次應用程式在其事件迴圈中有閒置時間。 此時，會刪除所有暫存的圖形物件。 換句話說，暫存物件只在一個視窗訊息處理期間有效。  
  
 如需使用圖形物件的詳細資訊，請參閱[圖形物件](http://msdn.microsoft.com/library/windows/desktop/dd144962)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CBrush::CBrush](#cbrush)。  
  
##  <a name="getlogbrush"></a>CBrush::GetLogBrush  
 呼叫此成員函式擷取`LOGBRUSH`結構。  
  
```  
int GetLogBrush(LOGBRUSH* pLogBrush);
```  
  
### <a name="parameters"></a>參數  
 `pLogBrush`  
 指向[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)包含筆刷的相關資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，和`pLogBrush`是有效的指標，傳回的值是儲存緩衝區的位元組數目。  
  
 如果函式成功，和`pLogBrush`是**NULL**，則傳回值是保留資訊的函式所需的位元組數目會儲存到緩衝區。  
  
 如果函式失敗，傳回值為 0。  
  
### <a name="remarks"></a>備註  
 `LOGBRUSH`結構會定義樣式、 色彩和筆刷的模式。  
  
 例如，呼叫`GetLogBrush`以符合特定色彩或圖樣的點陣圖。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&27;](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]  
  
##  <a name="operator_hbrush"></a>CBrush::operator HBRUSH  
 使用這個運算子來取得附加的 Windows GDI 控制代碼的`CBrush`物件。  
  
```  
operator HBRUSH() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，Windows GDI 物件的控制代碼所代表`CBrush`物件; 否則**NULL**。  
  
### <a name="remarks"></a>備註  
 這位操作員便轉型運算子，支援直接使用`HBRUSH`物件。  
  
 如需使用圖形物件的詳細資訊，請參閱[圖形物件](http://msdn.microsoft.com/library/windows/desktop/dd144962)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView #&28;](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 PROPDLG](../../visual-cpp-samples.md)   
 [CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CBitmap 類別](../../mfc/reference/cbitmap-class.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)

