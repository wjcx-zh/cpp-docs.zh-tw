---
title: CFont 類別
ms.date: 11/04/2016
f1_keywords:
- CFont
- AFXWIN/CFont
- AFXWIN/CFont::CFont
- AFXWIN/CFont::CreateFont
- AFXWIN/CFont::CreateFontIndirect
- AFXWIN/CFont::CreatePointFont
- AFXWIN/CFont::CreatePointFontIndirect
- AFXWIN/CFont::FromHandle
- AFXWIN/CFont::GetLogFont
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
ms.openlocfilehash: c37b2f657105e0065e0cddb2c508424bd6c89b0a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418619"
---
# <a name="cfont-class"></a>CFont 類別

封裝 Windows 繪圖裝置介面 (GDI) 字型並提供操作字型的成員函式。

## <a name="syntax"></a>語法

```
class CFont : public CGdiObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CFont：： CFont](#cfont)|建構 `CFont` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFont：： CreateFont](#createfont)|使用指定的特性，初始化 `CFont`。|
|[CFont：： CreateFontIndirect](#createfontindirect)|使用 `LOGFONT` 結構中提供的特性，初始化 `CFont` 物件。|
|[CFont：： CreatePointFont](#createpointfont)|初始化具有指定高度的 `CFont`，以十分之一的點和字樣來測量。|
|[CFont：： CreatePointFontIndirect](#createpointfontindirect)|與 `CreateFontIndirect` 相同，不同之處在于字型高度是以十分之一點（而非邏輯單元）來測量。|
|[CFont：： FromHandle](#fromhandle)|指定 Windows HFONT 時，傳回 `CFont` 物件的指標。|
|[CFont：： GetLogFont](#getlogfont)|以附加至 `CFont` 物件之邏輯字型的相關資訊，填滿 `LOGFONT`。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CFont：： operator HFONT](#operator_hfont)|傳回附加至 `CFont` 物件的 Windows GDI 字型控制碼。|

## <a name="remarks"></a>備註

若要使用 `CFont` 物件，請建立 `CFont` 物件，並使用[CreateFont](#createfont)、 [CreateFontIndirect](#createfontindirect)、 [CreatePointFont](#createpointfont)或[CreatePointFontIndirect](#createpointfontindirect)將 Windows 字型附加至它，然後使用物件的成員函式來操作字型。

`CreatePointFont` 和 `CreatePointFontIndirect` 函數通常會比 `CreateFont` 或 `CreateFontIndirect` 更容易使用，因為它們會自動從點大小轉換成邏輯單元的字型高度。

如需 `CFont`的詳細資訊，請參閱[繪圖物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cfont"></a>CFont：： CFont

建構 `CFont` 物件。

```
CFont();
```

### <a name="remarks"></a>備註

產生的物件必須使用 `CreateFont`、`CreateFontIndirect`、`CreatePointFont`或 `CreatePointFontIndirect` 來初始化，才能使用它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

##  <a name="createfont"></a>CFont：： CreateFont

使用指定的特性，初始化 `CFont` 物件。

```
BOOL CreateFont(
    int nHeight,
    int nWidth,
    int nEscapement,
    int nOrientation,
    int nWeight,
    BYTE bItalic,
    BYTE bUnderline,
    BYTE cStrikeOut,
    BYTE nCharSet,
    BYTE nOutPrecision,
    BYTE nClipPrecision,
    BYTE nQuality,
    BYTE nPitchAndFamily,
    LPCTSTR lpszFacename);
```

### <a name="parameters"></a>參數

*nHeight*<br/>
指定字型所需的高度（以邏輯單位表示）。 如需說明，請參閱 Windows SDK 中[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的 `lfHeight` 成員。 *NHeight*的絕對值在轉換後不得超過16384的裝置單位。 針對所有高度比較，字型對應工具會尋找不超過所要求大小的最大字型，如果所有字型超過要求的大小，則為最小的字型。

*nWidth*<br/>
指定字型中字元的平均寬度（以邏輯單位表示）。 如果*nWidth*為0，則裝置的外觀比例會與可用字型的數位化外觀比例進行比對，以尋找最接近的相符項，這取決於差異的絕對值。

*nEscapement*<br/>
指定在 [行距] 向量和顯示介面的 X 軸之間的角度（以0.1 度為單位）。 行距向量是指一行中第一個和最後一個字元的來源。 角度會從 X 軸逆時針測量。 如需詳細資訊，請參閱 Windows SDK 中 `LOGFONT` 結構的 `lfEscapement` 成員。

*nOrientation*<br/>
指定字元與 X 軸的基準之間的角度（以0.1 度為單位）。 角度是從 X 軸逆時針測量的座標系統，其中 y 方向是在 y 方向已啟動之座標系統的 X 軸下和順時針方向。

*nWeight*<br/>
指定字型粗細（以每1000的筆跡圖元為單位）。 如需詳細資訊，請參閱 Windows SDK 中 `LOGFONT` 結構的*lfWeight*成員。 描述的值為近似值;實際的外觀取決於字樣。 某些字型只有 FW_NORMAL、FW_REGULAR 和 FW_BOLD 權數。 如果指定 FW_DONTCARE，則會使用預設權數。

*bItalic*<br/>
指定字型是否為斜體。

*bUnderline*<br/>
指定字型是否加上底線。

*cStrikeOut*<br/>
指定字型中的字元是否為分行符號。如果設定為非零值，則指定刪除線字型。

*nCharSet*<br/>
指定字型的字元 setSee Windows SDK 中的 `LOGFONT` 結構中的 `lfCharSet` 成員，以取得值的清單。

OEM 字元集與系統相依。

具有其他字元集的字型可能存在於系統中。 使用具有未知字元集之字型的應用程式，不得嘗試轉譯或解讀要以該字型呈現的字串。 相反地，字串應該直接傳遞至輸出裝置磁碟機。

字型對應程式不會使用 DEFAULT_CHARSET 值。 應用程式可以使用此值來允許字型的名稱和大小，以完整描述邏輯字型。 如果具有指定名稱的字型不存在，則任何字元集中的字型都可以取代為指定的字型。 為了避免非預期的結果，應用程式應該謹慎使用 DEFAULT_CHARSET 值。

*nOutPrecision*<br/>
指定所需的輸出精確度。 輸出精確度會定義輸出必須符合所要求字型的高度、寬度、字元方向、行距和音調的程度。 如需值和詳細資訊的清單，請參閱 Windows SDK 中 `LOGFONT` 結構的 `lfOutPrecision` 成員。

*nClipPrecision*<br/>
指定所需的裁剪精確度。 裁剪精確度會定義如何裁剪部分在裁剪區域外的字元。 如需值清單，請參閱 Windows SDK 中 `LOGFONT` 結構的 `lfClipPrecision` 成員。

若要使用內嵌的唯讀字型，應用程式必須指定 CLIP_ENCAPSULATE。

若要達成裝置、TrueType 和向量字型的一致旋轉，應用程式可以使用 OR 運算子來結合 CLIP_LH_ANGLES 值與任何其他*nClipPrecision*值。 如果設定了 CLIP_LH_ANGLES 位，則所有字型的旋轉取決於座標系統的方向是向左或右手。 （如需座標系統方向的詳細資訊，請參閱*nOrientation*參數的描述）。如果未設定 CLIP_LH_ANGLES，裝置字型一律會逆時針旋轉，但其他字型的旋轉則取決於座標系統的方向。

*nQuality*<br/>
指定字型的輸出品質，以定義 GDI 必須嘗試將邏輯字型屬性與實際的實體字型進行比對的方式。 如需值清單，請參閱 Windows SDK 中 `LOGFONT` 結構的 `lfQuality` 成員。

*nPitchAndFamily*<br/>
指定字型的音調和系列。 如需值和詳細資訊的清單，請參閱 Windows SDK 中 `LOGFONT` 結構的 `lfPitchAndFamily` 成員。

*lpszFacename*<br/>
以 null 結束的字串 `CString` 或指標，指定字型的字樣名稱。 這個字串的長度不能超過30個字元。 Windows [EnumFontFamilies](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw)函數可用來列舉所有目前可用的字型。 如果*lpszFacename*為 Null，則 GDI 會使用與裝置無關的字樣。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

接著，字型可以選取為任何裝置內容的字型。

`CreateFont` 函數不會建立新的 Windows GDI 字型。 它只會從可供 GDI 使用的實體字型選取最接近的相符項。

建立邏輯字型時，應用程式可以使用大部分參數的預設設定。 應一律指定特定值的參數為*nHeight*和*lpszFacename*。 如果應用程式未設定*nHeight*和*lpszFacename* ，則建立的邏輯字型會與裝置相關。

當您完成 `CreateFont` 函數所建立的 `CFont` 物件時，請使用 `CDC::SelectObject` 在裝置內容中選取不同的字型，然後刪除不再需要的 `CFont` 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

##  <a name="createfontindirect"></a>CFont：： CreateFontIndirect

使用[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構中提供的特性，初始化 `CFont` 物件。

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>參數

*lpLogFont*<br/>
指向定義邏輯字型特性的 `LOGFONT` 結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

字型之後可以選取為任何裝置的目前字型。

此字型具有[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構中指定的特性。 使用[CDC：： SelectObject](../../mfc/reference/cdc-class.md#selectobject)成員函式選取字型時，GDI 字型對應程式會嘗試將邏輯字型與現有的實體字型比對。 如果字型對應工具找不到完全相符的邏輯字型，它會提供其特性與所要求的許多特性相符的替代字型。

當您不再需要由 `CreateFontIndirect` 函數所建立的 `CFont` 物件時，請使用 `CDC::SelectObject` 來選取裝置內容中的不同字型，然後刪除不再需要的 `CFont` 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

##  <a name="createpointfont"></a>CFont：： CreatePointFont

此函式提供簡單的方式來建立指定之字樣和點大小的字型。

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>參數

*nPointSize*<br/>
在十分之一點中要求的字型高度。 （例如，傳遞120以要求12點字型）。

*lpszFaceName*<br/>
以 null 結束的字串 `CString` 或指標，指定字型的字樣名稱。 這個字串的長度不能超過30個字元。 Windows ' EnumFontFamilies 函數可用來列舉所有目前可用的字型。 如果*lpszFaceName*為 Null，則 GDI 會使用與裝置無關的字樣。

*pDC*<br/>
要用來將*nPointSize*中的高度轉換成邏輯單元的[CDC](../../mfc/reference/cdc-class.md)物件指標。 如果是 Null，就會使用螢幕裝置內容進行轉換。

### <a name="return-value"></a>傳回值

如果成功，則為非零，否則為0。

### <a name="remarks"></a>備註

它會使用*pDC*所指向的 CDC 物件，自動將*nPointSize*中的高度轉換成邏輯單元。

當您完成 `CreatePointFont` 函式所建立的 `CFont` 物件時，請先選取裝置內容以外的字型，然後刪除 `CFont` 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

##  <a name="createpointfontindirect"></a>CFont：： CreatePointFontIndirect

此函式與[CreateFontIndirect](#createfontindirect)相同，不同之處在于 `LOGFONT` 的 `lfHeight` 成員會以十分之一點（而不是裝置單位）來解讀。

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>參數

*lpLogFont*<br/>
指向定義邏輯字型特性的[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構。 `LOGFONT` 結構的 `lfHeight` 成員是以十分之一點（而非邏輯單元）來測量。 （例如，將 `lfHeight` 設定為120，以要求12點字型）。

*pDC*<br/>
要用來將 `lfHeight` 中的高度轉換成邏輯單元的[CDC](../../mfc/reference/cdc-class.md)物件指標。 如果是 Null，就會使用螢幕裝置內容進行轉換。

### <a name="return-value"></a>傳回值

如果成功，則為非零，否則為0。

### <a name="remarks"></a>備註

此函式會在將 `LOGFONT` 結構傳遞至 Windows 之前，使用*pDC*所指向的 CDC 物件，自動將 `lfHeight` 中的高度轉換成邏輯單元。

當您完成 `CreatePointFontIndirect` 函式所建立的 `CFont` 物件時，請先選取裝置內容以外的字型，然後刪除 `CFont` 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

##  <a name="fromhandle"></a>CFont：： FromHandle

當提供 Windows GDI 字型物件的 HFONT 控制碼時，傳回 `CFont` 物件的指標。

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>參數

*hFont*<br/>
Windows 字型的 HFONT 控制碼。

### <a name="return-value"></a>傳回值

如果成功，則為 `CFont` 物件的指標;否則為 Null。

### <a name="remarks"></a>備註

如果 `CFont` 物件尚未附加至控制碼，則會建立並附加暫存 `CFont` 物件。 只有在下次應用程式的事件迴圈中有閒置時間時，才會將這個暫存 `CFont` 物件有效，此時所有的暫存繪圖物件都會被刪除。 另一個指出這種情況的方法是，暫存物件只在處理一個視窗訊息期間有效。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

##  <a name="getlogfont"></a>CFont：： GetLogFont

呼叫此函式可抓取 `CFont`的 `LOGFONT` 結構複本。

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>參數

*pLogFont*<br/>
要接收字型資訊之[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構的指標。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零，否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

##  <a name="operator_hfont"></a>CFont：： operator HFONT

使用這個運算子可取得附加至 `CFont` 物件之字型的 Windows GDI 控制碼。

```
operator HFONT() const;
```

### <a name="return-value"></a>傳回值

附加至 `CFont` 的 Windows GDI 字型物件的控制碼（如果成功）;否則為 Null。

### <a name="remarks"></a>備註

因為此運算子會自動用於從 `CFont` 轉換成字型[和文字](/windows/win32/gdi/fonts-and-text)，所以您可以將 `CFont` 物件傳遞至預期會 HFONTs 的函式。

如需使用繪圖物件的詳細資訊，請參閱 Windows SDK 中的[繪圖物件](/windows/win32/gdi/graphic-objects)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
