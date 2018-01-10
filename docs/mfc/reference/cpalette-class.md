---
title: "CPalette 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CPalette [MFC], CPalette
- CPalette [MFC], AnimatePalette
- CPalette [MFC], CreateHalftonePalette
- CPalette [MFC], CreatePalette
- CPalette [MFC], FromHandle
- CPalette [MFC], GetEntryCount
- CPalette [MFC], GetNearestPaletteIndex
- CPalette [MFC], GetPaletteEntries
- CPalette [MFC], ResizePalette
- CPalette [MFC], SetPaletteEntries
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 486338d579f304a6de1a54674a7711bb6c56f38c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cpalette-class"></a>CPalette 類別
封裝 Windows 調色盤。  
  
## <a name="syntax"></a>語法  
  
```  
class CPalette : public CGdiObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CPalette::CPalette](#cpalette)|建構`CPalette`物件沒有附加的 Windows 調色盤。 您必須先初始化`CPalette`物件使用初始化的成員函式才可以使用其中一個。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Cpalette:: Animatepalette](#animatepalette)|會取代調色盤中的邏輯所識別的項目`CPalette`物件。 應用程式不必更新其工作區，因為 Windows 立即對應系統調色盤將新項目。|  
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|建立裝置內容的半色調調色盤，並將它附加至`CPalette`物件。|  
|[CPalette::CreatePalette](#createpalette)|建立 Windows 色彩調色盤，並將它附加至`CPalette`物件。|  
|[CPalette::FromHandle](#fromhandle)|將指標傳回至`CPalette`物件控制代碼提供給 Windows 調色盤物件時。|  
|[CPalette::GetEntryCount](#getentrycount)|擷取邏輯的調色盤中的調色盤項目數目。|  
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|最接近的色彩值的邏輯調色盤中傳回的項目索引。|  
|[CPalette::GetPaletteEntries](#getpaletteentries)|擷取調色盤中的項目邏輯色板的範圍。|  
|[CPalette::ResizePalette](#resizepalette)|所指定的邏輯色板的大小變更`CPalette`物件指定的項目數目。|  
|[CPalette::SetPaletteEntries](#setpaletteentries)|RGB 色彩值和旗標範圍內設定邏輯調色盤中的項目。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[HPALETTE CPalette::operator](#operator_hpalette)|傳回`HPALETTE`附加至`CPalette`。|  
  
## <a name="remarks"></a>備註  
 調色盤提供應用程式和色彩輸出裝置 （例如顯示裝置） 之間的介面。 介面可讓應用程式以利用完整的色彩功能的輸出裝置，而不會嚴重妨礙的其他應用程式所顯示的色彩。 Windows 使用應用程式的邏輯色板 （所需的色彩清單） 和系統調色盤 （會定義可用的色彩） 來決定所使用的色彩。  
  
 A`CPalette`物件提供成員函式的物件操作調色盤參考。 建構`CPalette`物件，並使用其成員函式，以建立實際的調色盤，圖形裝置介面 (GDI) 物件，並管理它的項目和其他屬性。  
  
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
 指定要建立動畫的調色盤，第一個項目。  
  
 `nNumEntries`  
 若要建立動畫調色盤中指定的項目數。  
  
 `lpPaletteColors`  
 指向陣列的第一個成員[PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769)結構，以取代所識別的調色盤項目`nStartIndex`和`nNumEntries`。  
  
### <a name="remarks"></a>備註  
 當應用程式呼叫`AnimatePalette`，它並沒有要更新其工作區，因為 Windows 立即對應系統調色盤將新項目。  
  
 `AnimatePalette`函式只會變更的項目**PC_RESERVED**旗標設在對應**palPaletteEntry**隸屬[LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)結構附加至`CPalette`物件。 請參閱**LOGPALETTE** Windows SDK 中針對此結構的詳細資訊。  
  
##  <a name="cpalette"></a>CPalette::CPalette  
 建構 `CPalette` 物件。  
  
```  
CPalette();
```  
  
### <a name="remarks"></a>備註  
 物件有任何附加的調色盤，直到您呼叫`CreatePalette`將其中一個。  
  
##  <a name="createhalftonepalette"></a>CPalette::CreateHalftonePalette  
 建立裝置內容的半色調調色盤。  
  
```  
BOOL CreateHalftonePalette(CDC* pDC);
```  
  
### <a name="parameters"></a>參數  
 `pDC`  
 識別裝置內容。  
  
### <a name="return-value"></a>傳回值  
 如果函式成功則為非零，否則為 0。  
  
### <a name="remarks"></a>備註  
 當裝置內容的縮放模式設定為應用程式應該建立半色調調色盤**半色調**。 傳回邏輯半色調調色盤[CreateHalftonePalette](http://msdn.microsoft.com/library/windows/desktop/dd183503)成員函式應該然後選取並放入裝置內容，才能實現[CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)或[Stretchdibits 做](http://msdn.microsoft.com/library/windows/desktop/dd145121)呼叫函式。  
  
 請參閱 Windows SDK，如需詳細資訊，關於`CreateHalftonePalette`和**stretchdibits 做**。  
  
##  <a name="createpalette"></a>CPalette::CreatePalette  
 初始化`CPalette`藉由建立 Windows 邏輯調色盤，並將它來連接物件`CPalette`物件。  
  
```  
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```  
  
### <a name="parameters"></a>參數  
 `lpLogPalette`  
 指向[LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)結構，其中包含邏輯的調色盤色彩的相關資訊。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 請參閱 Windows SDK，如需詳細資訊，關於**LOGPALETTE**結構。  
  
##  <a name="fromhandle"></a>CPalette::FromHandle  
 將指標傳回至`CPalette`物件控制代碼提供給 Windows 調色盤物件時。  
  
```  
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```  
  
### <a name="parameters"></a>參數  
 `hPalette`  
 Windows GDI 色彩調色盤的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標`CPalette`物件，如果成功，否則**NULL**。  
  
### <a name="remarks"></a>備註  
 如果`CPalette`物件已經不附加到 Windows 調色盤，暫存`CPalette`物件會建立並附加。 此暫存`CPalette`僅直到下一次應用程式有其事件迴圈中的閒置時間，在這次所有暫存圖形已刪除物件，物件才有效。 換句話說，暫存物件只在一個視窗訊息的處理期間有效。  
  
##  <a name="getentrycount"></a>CPalette::GetEntryCount  
 呼叫此成員函式可擷取的物件中指定的邏輯色板的項目數目。  
  
```  
int GetEntryCount();
```  
  
### <a name="return-value"></a>傳回值  
 邏輯調色盤中的項目數。  
  
##  <a name="getnearestpaletteindex"></a>CPalette::GetNearestPaletteIndex  
 邏輯調色盤最符合指定的色彩值中傳回的項目索引。  
  
```  
UINT GetNearestPaletteIndex(COLORREF crColor) const;  
```  
  
### <a name="parameters"></a>參數  
 `crColor`  
 指定要比對的色彩。  
  
### <a name="return-value"></a>傳回值  
 邏輯調色盤中的項目索引。 項目包含最幾乎符合指定的色彩的色彩。  
  
##  <a name="getpaletteentries"></a>CPalette::GetPaletteEntries  
 擷取調色盤中的項目邏輯色板的範圍。  
  
```  
UINT GetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors) const;  
```  
  
### <a name="parameters"></a>參數  
 `nStartIndex`  
 指定要擷取邏輯的調色盤中的第一個項目。  
  
 `nNumEntries`  
 要擷取邏輯的調色盤中指定的項目數。  
  
 `lpPaletteColors`  
 指向陣列[PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769)資料結構，以接收調色盤項目。 陣列必須包含所指定的數目，至少資料結構`nNumEntries`。  
  
### <a name="return-value"></a>傳回值  
 從邏輯色板; 擷取的項目數目如果函式失敗，，0。  
  
##  <a name="operator_hpalette"></a>HPALETTE CPalette::operator  
 使用此運算子，以取得附加的 Windows GDI 控制代碼的`CPalette`物件。  
  
```  
operator HPALETTE() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，Windows GDI 物件的控制代碼來表示`CPalette`物件; 否則**NULL**。  
  
### <a name="remarks"></a>備註  
 這位操作員便轉型運算子，可支援直接使用`HPALETTE`物件。  
  
 如需使用 圖形物件的詳細資訊，請參閱文章[圖形物件](http://msdn.microsoft.com/library/windows/desktop/dd144962)Windows SDK 中。  
  
##  <a name="resizepalette"></a>CPalette::ResizePalette  
 變更附加到邏輯色板的大小`CPalette`物件所指定的項目數`nNumEntries`。  
  
```  
BOOL ResizePalette(UINT nNumEntries);
```  
  
### <a name="parameters"></a>參數  
 `nNumEntries`  
 已調整大小之後，調色盤中指定的項目數。  
  
### <a name="return-value"></a>傳回值  
 如果已成功調整調色盤; 非零，否則便是 0。  
  
### <a name="remarks"></a>備註  
 如果應用程式呼叫`ResizePalette`以減少大小的調色盤，剩餘大小經過調整的調色盤中的項目維持不變。 如果應用程式呼叫`ResizePalette`為加大調色盤，其他調色盤項目則設定為黑色 （紅色、 綠色和藍色值會是所有 0），以及所有其他項目的旗標都會設為 0。  
  
 如需有關 Windows API `ResizePalette`，請參閱[ResizePalette](http://msdn.microsoft.com/library/windows/desktop/dd162928) Windows SDK 中。  
  
##  <a name="setpaletteentries"></a>CPalette::SetPaletteEntries  
 RGB 色彩值和旗標範圍內設定邏輯調色盤中的項目。  
  
```  
UINT SetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>參數  
 `nStartIndex`  
 指定第一個項目設定邏輯的調色盤。  
  
 `nNumEntries`  
 設定邏輯調色盤中指定的項目數。  
  
 `lpPaletteColors`  
 指向陣列[PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769)資料結構，以接收調色盤項目。 陣列必須包含所指定的數目，至少資料結構`nNumEntries`。  
  
### <a name="return-value"></a>傳回值  
 設定邏輯調色盤; 中的項目數目如果函式失敗，，0。  
  
### <a name="remarks"></a>備註  
 如果邏輯色板會放入裝置內容中時選取應用程式呼叫`SetPaletteEntries`，變更將不會生效，直到應用程式呼叫[CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)。  
  
 如需有關 Windows 結構**PALETTEENTRY**，請參閱[PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) Windows SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [MFC 範例 DIBLOOK](../../visual-cpp-samples.md)   
 [CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CPalette::GetPaletteEntries](#getpaletteentries)   
 [CPalette::SetPaletteEntries](#setpaletteentries)



