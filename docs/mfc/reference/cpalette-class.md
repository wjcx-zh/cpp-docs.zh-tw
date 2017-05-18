---
title: "CPalette 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPalette
- AFXWIN/CPalette
- AFXWIN/CPalette::CPalette
- AFXWIN/CPalette::AnimatePalette
- AFXWIN/CPalette::CreateHalftonePalette
- AFXWIN/CPalette::CreatePalette
- AFXWIN/CPalette::FromHandle
- AFXWIN/CPalette::GetEntryCount
- AFXWIN/CPalette::GetNearestPaletteIndex
- AFXWIN/CPalette::GetPaletteEntries
- AFXWIN/CPalette::ResizePalette
- AFXWIN/CPalette::SetPaletteEntries
dev_langs:
- C++
helpviewer_keywords:
- CPalette class
- HPALETTE
- color palettes, MFC
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
caps.latest.revision: 23
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
ms.openlocfilehash: 6ccd389eaf765993c59311cc1041893f2cf9fbfa
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cpalette-class"></a>CPalette 類別
封裝 Windows 調色盤。  
  
## <a name="syntax"></a>語法  
  
```  
class CPalette : public CGdiObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CPalette::CPalette](#cpalette)|建構`CPalette`物件沒有附加的 Windows 調色盤。 您必須先初始化`CPalette`物件與其中一個成員函式初始化才能使用。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Cpalette:: Animatepalette](#animatepalette)|取代項目中所識別的邏輯調色盤`CPalette`物件。 應用程式並沒有更新其工作區，因為 Windows 對應立即將新的項目變成系統調色盤。|  
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|建立裝置內容的半色調調色盤並將它附加`CPalette`物件。|  
|[CPalette::CreatePalette](#createpalette)|建立 Windows 調色盤並將它附加`CPalette`物件。|  
|[CPalette::FromHandle](#fromhandle)|若要將指標傳回`CPalette`物件控制代碼給 Windows 調色盤物件時。|  
|[CPalette::GetEntryCount](#getentrycount)|擷取調色盤邏輯調色盤中的項目的數目。|  
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|最接近的色彩值的邏輯調色盤中傳回的項目索引。|  
|[CPalette::GetPaletteEntries](#getpaletteentries)|擷取各種調色盤邏輯調色盤中的項目。|  
|[CPalette::ResizePalette](#resizepalette)|變更大小所指定的邏輯調色盤`CPalette`物件指定的項目數目。|  
|[CPalette::SetPaletteEntries](#setpaletteentries)|設定邏輯調色盤中的項目範圍中的 RGB 色彩值和旗標。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CPalette::operator HPALETTE](#operator_hpalette)|傳回`HPALETTE`附加至`CPalette`。|  
  
## <a name="remarks"></a>備註  
 調色盤提供應用程式與色彩輸出裝置 （例如顯示裝置） 之間的介面。 介面可讓應用程式以充分利用輸出裝置的色彩功能而不會嚴重妨礙其他應用程式所顯示的色彩。 Windows 會使用應用程式的邏輯調色盤 （所需的色彩清單） 和系統調色盤 （會定義可用的色彩） 來判斷所使用的色彩。  
  
 A`CPalette`物件提供成員函式的物件操作調色盤參考。 建構`CPalette`物件，並將其成員函式來建立實際的調色盤，圖形裝置介面 (GDI) 物件，並管理其項目和其他屬性。  
  
 如需有關使用`CPalette`，請參閱[圖形物件](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPalette`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="animatepalette"></a>Cpalette:: Animatepalette  
 取代附加至邏輯調色盤中的項目`CPalette`物件。  
  
```  
void AnimatePalette(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>參數  
 `nStartIndex`  
 指定以動畫顯示調色盤中的第一個項目。  
  
 `nNumEntries`  
 以動畫顯示調色盤中指定的項目數。  
  
 `lpPaletteColors`  
 指向陣列的第一個成員[PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769)結構，以取代所識別的調色盤項目`nStartIndex`和`nNumEntries`。  
  
### <a name="remarks"></a>備註  
 當應用程式呼叫`AnimatePalette`，它並沒有要更新其工作區，因為 Windows 對應立即將新的項目變成系統調色盤。  
  
 `AnimatePalette`函式只會變更的項目**PC_RESERVED**旗標設在對應**palPaletteEntry**成員[LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)結構連接至`CPalette`物件。 請參閱**LOGPALETTE**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需有關此結構。  
  
##  <a name="cpalette"></a>CPalette::CPalette  
 建構 `CPalette` 物件。  
  
```  
CPalette();
```  
  
### <a name="remarks"></a>備註  
 物件會有任何附加的調色盤，直到您呼叫`CreatePalette`附加一個。  
  
##  <a name="createhalftonepalette"></a>CPalette::CreateHalftonePalette  
 建立裝置內容的半色調調色盤。  
  
```  
BOOL CreateHalftonePalette(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 識別的裝置內容。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 當裝置內容的縮放模式設為應用程式應建立半色調調色盤**半色調**。 傳回邏輯半色調調色盤[CreateHalftonePalette](http://msdn.microsoft.com/library/windows/desktop/dd183503)成員函式應該然後選取並放入裝置內容之前實現[CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)或[stretchdibits 做](http://msdn.microsoft.com/library/windows/desktop/dd145121)函式呼叫。  
  
 請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊`CreateHalftonePalette`和**stretchdibits 做**。  
  
##  <a name="createpalette"></a>CPalette::CreatePalette  
 初始化`CPalette`藉由建立 Windows 邏輯調色盤，並附加至物件`CPalette`物件。  
  
```  
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```  
  
### <a name="parameters"></a>參數  
 `lpLogPalette`  
 指向[LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)結構，其中包含邏輯調色盤色彩的相關資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]如需詳細資訊**LOGPALETTE**結構。  
  
##  <a name="fromhandle"></a>CPalette::FromHandle  
 若要將指標傳回`CPalette`物件控制代碼給 Windows 調色盤物件時。  
  
```  
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```  
  
### <a name="parameters"></a>參數  
 `hPalette`  
 Windows GDI 調色盤控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標`CPalette`物件如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果`CPalette`物件尚未附加至 Windows 調色盤，暫存`CPalette`會建立並附加物件。 此暫存`CPalette`僅直到下一次應用程式在其事件迴圈中有閒置時間，在這次所有暫存圖形會刪除物件，物件才有效。 換句話說，暫存物件只在一個視窗訊息處理期間有效。  
  
##  <a name="getentrycount"></a>CPalette::GetEntryCount  
 呼叫此成員函式擷取指定的邏輯調色盤中的項目數。  
  
```  
int GetEntryCount();
```  
  
### <a name="return-value"></a>傳回值  
 邏輯調色盤中的項目數。  
  
##  <a name="getnearestpaletteindex"></a>CPalette::GetNearestPaletteIndex  
 最接近指定的色彩值的邏輯調色盤中傳回的項目索引。  
  
```  
UINT GetNearestPaletteIndex(COLORREF crColor) const;  
```  
  
### <a name="parameters"></a>參數  
 `crColor`  
 指定要比對的色彩。  
  
### <a name="return-value"></a>傳回值  
 邏輯調色盤中的項目索引。 項目包含最幾乎符合指定的色彩的色彩。  
  
##  <a name="getpaletteentries"></a>CPalette::GetPaletteEntries  
 擷取各種調色盤邏輯調色盤中的項目。  
  
```  
UINT GetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors) const;  
```  
  
### <a name="parameters"></a>參數  
 `nStartIndex`  
 指定要擷取邏輯調色盤中的第一個項目。  
  
 `nNumEntries`  
 要擷取邏輯調色盤中指定的項目數。  
  
 `lpPaletteColors`  
 指向陣列[PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769)資料結構，以接收調色盤項目。 陣列必須包含至少盡所指定的資料結構`nNumEntries`。  
  
### <a name="return-value"></a>傳回值  
 從邏輯調色盤; 擷取的項目數目0，表示失敗的函式。  
  
##  <a name="operator_hpalette"></a>CPalette::operator HPALETTE  
 使用這個運算子來取得附加的 Windows GDI 控制代碼的`CPalette`物件。  
  
```  
operator HPALETTE() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，Windows GDI 物件的控制代碼所代表`CPalette`物件; 否則**NULL**。  
  
### <a name="remarks"></a>備註  
 這位操作員便轉型運算子，支援直接使用`HPALETTE`物件。  
  
 如需使用圖形物件的詳細資訊，請參閱文章[圖形物件](http://msdn.microsoft.com/library/windows/desktop/dd144962)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="resizepalette"></a>CPalette::ResizePalette  
 變更大小，連接到的邏輯調色盤`CPalette`物件所指定的項目數`nNumEntries`。  
  
```  
BOOL ResizePalette(UINT nNumEntries);
```  
  
### <a name="parameters"></a>參數  
 `nNumEntries`  
 已調整大小之後，調色盤中指定的項目數。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功調整調色盤;否則為 0。  
  
### <a name="remarks"></a>備註  
 如果應用程式呼叫`ResizePalette`可縮小的調色盤，剩餘調整調色盤中的項目是不變。 如果應用程式呼叫`ResizePalette`擴大調色盤，其他調色盤項目已設定為黑色 （紅色、 綠色和藍色值是所有的 0），以及所有其他項目的旗標會設為 0。  
  
 如需有關 Windows API `ResizePalette`，請參閱[ResizePalette](http://msdn.microsoft.com/library/windows/desktop/dd162928)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setpaletteentries"></a>CPalette::SetPaletteEntries  
 設定邏輯調色盤中的項目範圍中的 RGB 色彩值和旗標。  
  
```  
UINT SetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>參數  
 `nStartIndex`  
 設定邏輯調色盤中，指定第一個項目。  
  
 `nNumEntries`  
 若要設定邏輯調色盤中指定的項目數。  
  
 `lpPaletteColors`  
 指向陣列[PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769)資料結構，以接收調色盤項目。 陣列必須包含至少盡所指定的資料結構`nNumEntries`。  
  
### <a name="return-value"></a>傳回值  
 設定邏輯調色盤; 中的項目數0，表示失敗的函式。  
  
### <a name="remarks"></a>備註  
 當應用程式呼叫時，如果要邏輯調色盤選取放入裝置內容`SetPaletteEntries`，變更將不會生效，直到應用程式呼叫[CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)。  
  
 如需有關 Windows 結構**PALETTEENTRY**，請參閱[PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 DIBLOOK](../../visual-cpp-samples.md)   
 [CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPalette::GetPaletteEntries](#getpaletteentries)   
 [CPalette::SetPaletteEntries](#setpaletteentries)




