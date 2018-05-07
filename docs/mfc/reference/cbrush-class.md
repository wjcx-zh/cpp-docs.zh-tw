---
title: CBrush 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39c5167c81d6c44fa62f9bff87c6c04f73f9f6d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cbrush-class"></a>CBrush 類別
封裝 Windows 繪圖裝置介面 (GDI) 筆刷。  
  
## <a name="syntax"></a>語法  
  
```  
class CBrush : public CGdiObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CBrush::CBrush](#cbrush)|建構 `CBrush` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CBrush::CreateBrushIndirect](#createbrushindirect)|初始化與樣式、 色彩和模式中指定的筆刷[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)結構。|  
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|使用裝置獨立點陣圖 (DIB) 所指定的模式，初始化筆刷。|  
|[CBrush::CreateHatchBrush](#createhatchbrush)|初始化具有指定影線的模式和色彩的筆刷。|  
|[CBrush::CreatePatternBrush](#createpatternbrush)|指定點陣圖的模式，初始化筆刷。|  
|[CBrush::CreateSolidBrush](#createsolidbrush)|初始化具有指定的單色筆刷。|  
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|建立為預設系統色彩的筆刷。|  
|[CBrush::FromHandle](#fromhandle)|將指標傳回至`CBrush`物件時指定的 windows 控制代碼`HBRUSH`物件。|  
|[CBrush::GetLogBrush](#getlogbrush)|取得[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)結構。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[HBRUSH CBrush::operator](#operator_hbrush)|傳回附加至的 Windows 控制代碼`CBrush`物件。|  
  
## <a name="remarks"></a>備註  
 若要使用`CBrush`物件，然後建構`CBrush`物件，並將它傳遞至任何`CDC`需要筆刷的成員函式。  
  
 影線，或以月份為模式，可以是實線、 筆刷。  
  
 如需有關`CBrush`，請參閱[圖形物件](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBrush`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cbrush"></a>  CBrush::CBrush  
 建構 `CBrush` 物件。  
  
```  
CBrush(); 
CBrush(COLORREF crColor); 
CBrush(int nIndex, COLORREF crColor); 
explicit CBrush(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>參數  
 `crColor`  
 指定做為 RGB 色彩的筆刷的前景色彩。 如果影線筆刷，這個參數會指定影線色彩。  
  
 `nIndex`  
 指定的筆刷的影線類型。 它可以是下列值之一：  
  
- `HS_BDIAGONAL` 在 45 度向下串聯 （由左到右）  
  
- `HS_CROSS` 水平和垂直有斜紋  
  
- `HS_DIAGCROSS` Crosshatch 45 度角  
  
- `HS_FDIAGONAL` 在 45 度向上串聯 （由左到右）  
  
- `HS_HORIZONTAL` 水平影線  
  
- `HS_VERTICAL` 垂直影線  
  
 `pBitmap`  
 指向`CBitmap`物件，指定與筆刷繪製的點陣圖。  
  
### <a name="remarks"></a>備註  
 `CBrush` 有四個多載建構函式。不使用引數的建構函式會建構未初始化`CBrush`必須初始化，才能使用的物件。  
  
 如果您使用不含引數的建構函式，您必須初始化產生`CBrush`物件[CreateSolidBrush](#createsolidbrush)， [CreateHatchBrush](#createhatchbrush)， [CreateBrushIndirect](#createbrushindirect)， [CreatePatternBrush](#createpatternbrush)，或[CreateDIBPatternBrush](#createdibpatternbrush)。 如果您使用其中一個會採用引數的建構函式，則不進行任何初始化不需要。 如果發生錯誤，而不使用引數的建構函式一定會成功，則引數的建構函式會擲回例外狀況。  
  
 建構函式具有單一[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)參數建構實心筆刷使用指定的色彩。 指定 RGB 值的色彩，以及可以使用建構`RGB`WINDOWS 中的巨集。H.  
  
 具有兩個參數的建構函式會建構規劃筆刷。 `nIndex`參數指定的索引影線圖樣。 `crColor`參數指定的色彩。  
  
 建構函式`CBitmap`參數建構圖樣的筆刷。 參數會識別點陣圖。 點陣圖會假設已經建立使用[CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)， [Bitmap](../../mfc/reference/cbitmap-class.md#createbitmapindirect)， [cbitmap:: Loadbitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)，或[CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)。 點陣圖，用於填滿模式中的最小大小是 8 x 8 像素。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]  
  
##  <a name="createbrushindirect"></a>  CBrush::CreateBrushIndirect  
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
 接著為目前的筆刷的任何裝置的內容中選取筆刷。  
  
 使用目前的文字和背景色彩繪製使用 1 平面 （每個像素的 1 位元） 的單色點陣圖建立筆刷。 由位元設為 0 的像素為單位的外觀將與目前的文字色彩。 使用目前的背景色彩來繪製由位元設為 1 的像素為單位。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]  
  
##  <a name="createdibpatternbrush"></a>  CBrush::CreateDIBPatternBrush  
 使用指定的裝置獨立點陣圖 (DIB) 的模式，初始化筆刷。  
  
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
 識別包含壓縮的裝置獨立點陣圖 (DIB) 的全域記憶體物件。  
  
 *nUsage*  
 指定是否**bmiColors []** 欄位[BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md)資料結構 （屬於 「 封裝 DIB 」） 到目前實現邏輯色板包含明確的 RGB 值或索引。 參數必須是下列值之一：  
  
- **DIB_PAL_COLORS**色彩表包含 16 位元索引的陣列。  
  
- **DIB_RGB_COLORS**色彩表包含常值的 RGB 值。  
  
 *lpPackedDIB*  
 指向組成壓縮 DIB`BITMAPINFO`緊接著定義點陣圖的像素的位元組陣列的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 接著選取筆刷為任何支援點陣作業的裝置內容。  
  
 處理 DIB 方式在兩個版本各有不同：  
  
-   在第一個版本中，若要取得的控制代碼 DIB 您呼叫 Windows **GlobalAlloc**函式來配置全域記憶體區塊，並再將記憶體填入壓縮 DIB。  
  
-   在第二個版本，就不需要呼叫**GlobalAlloc**壓縮 DIB 配置記憶體。  
  
 壓縮的 DIB 組成`BITMAPINFO`緊接著定義點陣圖的像素的位元組陣列的資料結構。 點陣圖做為填滿模式應該是 8 x 8 像素。 如果點陣圖較大，Windows 會建立使用對應的前 8 的資料列和 8 的資料行的點陣圖左上角像素的位元的填滿模式。  
  
 當應用程式放入單色裝置內容中，選取兩個色彩 DIB 模式筆刷時，Windows 會忽略 DIB 中指定的色彩，並改為顯示 使用目前的文字和背景色彩的裝置內容的模式筆刷。 使用的文字色彩來顯示對應到 DIB （在 DIB 色彩表中的位移 0） 的第一個色彩的像素為單位。 使用的背景色彩來顯示對應到 （在色彩表中的位移 1） 的第二個色彩的像素為單位。  
  
 使用下列 Windows 功能的相關資訊，請參閱 Windows SDK:  
  
- [CreateDIBPatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183492) (僅針對相容性的 Windows 版本早於 3.0 撰寫的應用程式中提供此函式，使用**CreateDIBPatternBrushPt**函式。)  
  
- [CreateDIBPatternBrushPt](http://msdn.microsoft.com/library/windows/desktop/dd183493) （這個函式應使用的 win32 應用程式）。  
  
- [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]  
  
##  <a name="createhatchbrush"></a>  CBrush::CreateHatchBrush  
 初始化具有指定影線的模式和色彩的筆刷。  
  
```  
BOOL CreateHatchBrush(
    int nIndex,  
    COLORREF crColor);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定的筆刷的影線類型。 它可以是下列值之一：  
  
- `HS_BDIAGONAL` 在 45 度向下串聯 （由左到右）  
  
- `HS_CROSS` 水平和垂直有斜紋  
  
- `HS_DIAGCROSS` Crosshatch 45 度角  
  
- `HS_FDIAGONAL` 在 45 度向上串聯 （由左到右）  
  
- `HS_HORIZONTAL` 水平影線  
  
- `HS_VERTICAL` 垂直影線  
  
 `crColor`  
 指定前景色彩的筆刷做為 RGB 色彩 （影線色彩）。 請參閱[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)如需詳細資訊的 Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 接著為目前的筆刷的任何裝置的內容中選取筆刷。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]  
  
##  <a name="createpatternbrush"></a>  CBrush::CreatePatternBrush  
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
 接著選取筆刷為任何支援點陣作業的裝置內容。 所識別的點陣圖`pBitmap`通常會藉由使用初始化[CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)， [Bitmap](../../mfc/reference/cbitmap-class.md#createbitmapindirect)， [cbitmap:: Loadbitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)，或[CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)函式。  
  
 點陣圖做為填滿模式應該是 8 x 8 像素。 如果點陣圖大時，Windows 只會使用對應的前 8 個資料列和資料行的點陣圖左上角像素的位元。  
  
 可以刪除模式筆刷，而不會影響相關聯的點陣圖。 這表示點陣圖可以用來建立任意數目的模式筆刷。  
  
 使用目前的文字和背景色彩繪製使用單色點陣圖 （1 色彩平面，每個像素的 1 位元） 所建立的筆刷。 像素的位元設為 0 表示會使用目前的文字色彩繪製。 像素為單位由位元設為 1 會使用目前的背景色彩繪製。  
  
 如需使用[CreatePatternBrush](http://msdn.microsoft.com/library/windows/desktop/dd183508)，Windows 函式，請參閱 Windows SDK。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]  
  
##  <a name="createsolidbrush"></a>  CBrush::CreateSolidBrush  
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
 接著為目前的筆刷的任何裝置的內容中選取筆刷。  
  
 當應用程式已經完成使用所建立的筆刷`CreateSolidBrush`，它應該選取完裝置內容的筆刷。  
  
### <a name="example"></a>範例  
  請參閱範例的[CBrush::CBrush](#cbrush)。  
  
##  <a name="createsyscolorbrush"></a>  CBrush::CreateSysColorBrush  
 初始化筆刷色彩。  
  
```  
BOOL CreateSysColorBrush(int nIndex);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 指定的色彩索引。 此值對應至用來繪製其中 21 視窗元素的色彩。 請參閱[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)值清單的 Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 接著為目前的筆刷的任何裝置的內容中選取筆刷。  
  
 當應用程式已經完成使用所建立的筆刷`CreateSysColorBrush`，它應該選取完裝置內容的筆刷。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]  
  
##  <a name="fromhandle"></a>  CBrush::FromHandle  
 將指標傳回至`CBrush`物件時指定的 windows 控制代碼[HBRUSH](#operator_hbrush)物件。  
  
```  
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```  
  
### <a name="parameters"></a>參數  
 `hBrush`  
 `HANDLE` 為 Windows GDI 筆刷。  
  
### <a name="return-value"></a>傳回值  
 指標`CBrush`物件，如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果`CBrush`物件未附加至控制代碼，暫存`CBrush`物件會建立並附加。 此暫存`CBrush`物件是否有效，只到下一次應用程式在其事件迴圈中有閒置時間。 在這個階段中，會刪除所有暫存的圖形物件。 換句話說，暫存物件只在一個視窗訊息的處理期間有效。  
  
 如需有關使用圖形物件的詳細資訊，請參閱[圖形物件](http://msdn.microsoft.com/library/windows/desktop/dd144962)Windows SDK 中。  
  
### <a name="example"></a>範例  
  請參閱範例的[CBrush::CBrush](#cbrush)。  
  
##  <a name="getlogbrush"></a>  CBrush::GetLogBrush  
 呼叫此成員函式可擷取`LOGBRUSH`結構。  
  
```  
int GetLogBrush(LOGBRUSH* pLogBrush);
```  
  
### <a name="parameters"></a>參數  
 `pLogBrush`  
 指向[LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035)包含筆刷的相關資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功，和`pLogBrush`是有效的指標，傳回值是儲存在緩衝區的位元組數。  
  
 如果函式成功，和`pLogBrush`是**NULL**，則傳回值是保存的資訊函式所需的位元組數目會儲存在緩衝區。  
  
 如果函式失敗，傳回的值為 0。  
  
### <a name="remarks"></a>備註  
 `LOGBRUSH`結構會定義樣式、 色彩和筆刷的模式。  
  
 例如，呼叫`GetLogBrush`以符合特定色彩或圖樣的點陣圖。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]  
  
##  <a name="operator_hbrush"></a>  HBRUSH CBrush::operator  
 使用此運算子，以取得附加的 Windows GDI 控制代碼的`CBrush`物件。  
  
```  
operator HBRUSH() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，Windows GDI 物件的控制代碼來表示`CBrush`物件; 否則**NULL**。  
  
### <a name="remarks"></a>備註  
 這位操作員便轉型運算子，可支援直接使用`HBRUSH`物件。  
  
 如需有關使用圖形物件的詳細資訊，請參閱[圖形物件](http://msdn.microsoft.com/library/windows/desktop/dd144962)Windows SDK 中。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 PROPDLG](../../visual-cpp-samples.md)   
 [CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CBitmap 類別](../../mfc/reference/cbitmap-class.md)   
 [CDC 類別](../../mfc/reference/cdc-class.md)
