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
ms.openlocfilehash: 36fd469b182d5f3e0d3449112d04c1a8623d7526
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373835"
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
|[CFont:CFont](#cfont)|建構 `CFont` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CFont::建立字型](#createfont)|使用指定的特徵初始`CFont`化 。|
|[CFont::創建字體間接](#createfontindirect)|初始化具有`CFont``LOGFONT`結構中給出的特徵的物件。|
|[CFont::建立點字型](#createpointfont)|初始化具有`CFont`指定高度(以點數的十分之一和字體為單位)。|
|[CFont::創建點字體間接](#createpointfontindirect)|與`CreateFontIndirect`字體高度以點數而不是邏輯單位為單位度量的情況相同。|
|[CFont::從手柄](#fromhandle)|在給定 Windows `CFont` HFONT 時返回指向物件的指標。|
|[CFont::取得紀錄字型](#getlogfont)|`LOGFONT`填充有關附加到`CFont`物件的邏輯字體的資訊。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CFont::操作員惠普](#operator_hfont)|返回附加到`CFont`物件的 Windows GDI 字體句柄。|

## <a name="remarks"></a>備註

要使用`CFont`物件,請建構`CFont`物件 並將 Windows 字體與[CreateFont、CreateFont](#createfont)[間接](#createfontindirect)、創建 PointFont 或[CreatePointFont 間接](#createpointfontindirect)一起附加到物件,[CreatePointFont](#createpointfont)然後使用物件的成員函數操作該字體。

`CreatePointFont`和`CreatePointFontIndirect`函數通常`CreateFont`比`CreateFontIndirect`或因為它們自動將字體的高度從點大小轉換為邏輯單位更容易使用。

有關 的詳細`CFont`資訊 ,請參閱[圖形物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cfontcfont"></a><a name="cfont"></a>CFont:CFont

建構 `CFont` 物件。

```
CFont();
```

### <a name="remarks"></a>備註

生成的物件必須`CreateFont`用 初始`CreateFontIndirect`化`CreatePointFont`為`CreatePointFontIndirect`、 , 或在使用它之前。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

## <a name="cfontcreatefont"></a><a name="createfont"></a>CFont::建立字型

初始化具有指定`CFont`特徵的物件。

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
指定字體所需的高度(以邏輯單位為單位)。 有關說明`lfHeight`,請參閱 Windows SDK 中的[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構成員。 *nHeight*的絕對值在轉換後不得超過 16,384 個設備單位。 對於所有高度比較,如果所有字體都超過請求的大小,則字體映射器查找不超過請求大小或最小字體的最大字體。

*n 寬度*<br/>
指定字體中字元的平均寬度(以邏輯單位為單位)。 如果*nWidth*為 0,則設備的縱橫比將與可用字體的數位化縱橫比匹配,以查找最接近的匹配項,該匹配由差值的絕對值決定。

*n 逃生*<br/>
指定轉義向量與顯示曲面的 x 軸之間的角度(以 0.1 度為單位)。 轉義向量是行上第一個和最後一個字元的原點。 角度從 x 軸逆時針測量。 有關詳細資訊,`lfEscapement`請參閱`LOGFONT`Windows SDK 結構中的成員。

*n定向*<br/>
指定字元基線和 x 軸之間的角度(以 0.1 度為單位)。 角度從 y 方向向下的座標系的 x 軸逆時針測量,從 y 方向向上的座標系的 x 軸順時針。

*n 重量*<br/>
指定字體粗細(每 1000 個以墨分像素為單位)。 有關詳細資訊,請參閱 Windows SDK`LOGFONT`結構中的*lfWeight*成員。 描述的值是近似值;實際外觀取決於字體。 某些字體僅具有FW_NORMAL、FW_REGULAR和FW_BOLD權重。 如果指定FW_DONTCARE,則使用預設權重。

*比塔利奇*<br/>
指定字型是否為斜體。

*b 下線*<br/>
指定字型是否帶有下劃線。

*cStrikeOut*<br/>
指定是否已退出字型中的字元。如果設置為非零值,則指定刪除字體。

*nCharSet*<br/>
指定字型的字元集 查看`lfCharSet`Windows`LOGFONT`SDK 結構中的成員,瞭解值清單。

OEM 字元集與系統相關。

系統中可能存在具有其他字元集的字體。 使用具有未知字元集的字型的應用程式不得嘗試轉換或解釋要用該字體呈現的字串。 相反,字串應直接傳遞到輸出設備驅動程式。

字體對應器不使用DEFAULT_CHARSET值。 應用程式可以使用此值允許字體的名稱和大小來完全描述邏輯字體。 如果不存在具有指定名稱的字型,則可以將任何字元集中的字體替換為指定的字型。 為了避免意外結果,應用程式應謹慎使用DEFAULT_CHARSET值。

*nOut精度*<br/>
指定所需的輸出精度。 輸出精度定義輸出必須與請求的字型的高度、寬度、字元方向、轉義和間距的匹配程度。 有關值`lfOutPrecision`的清單和詳細資訊`LOGFONT`,請參閱 Windows SDK 結構中的成員。

*nClip 精度*<br/>
指定所需的剪切精度。 裁剪精度定義如何剪輯部分超出剪輯區域的字元。 有關值`lfClipPrecision`清單`LOGFONT`, 請參閱 Windows SDK 結構中的成員。

要使用嵌入的唯讀字型,應用程式必須指定CLIP_ENCAPSULATE。

為了實現設備、TrueType 和向量字型的一致旋轉,應用程式可以使用 OR 運算符將CLIP_LH_ANGLES值與任何其他*nClipPrecision*值合併。 如果設置了CLIP_LH_ANGLES位,則所有字體的旋轉取決於座標系的方向是左手還是右手。 (有關座標系方向的詳細資訊,請參閱*n方向*參數的說明。如果未設置CLIP_LH_ANGLES,則設備字體始終逆時針旋轉,但其他字體的旋轉取決於座標系的方向。

*n 品質*<br/>
指定字體的輸出品質,該品質定義 GDI 必須仔細嘗試將邏輯字體屬性與實際物理字體的屬性相匹配。 有關值`lfQuality`清單`LOGFONT`, 請參閱 Windows SDK 結構中的成員。

*n 皮奇和家庭*<br/>
指定字體的間距和族。 有關值`lfPitchAndFamily`的清單和詳細資訊`LOGFONT`,請參閱 Windows SDK 結構中的成員。

*lpszFace 名稱*<br/>
指向`CString`null 連接端的字串的或指標,該字串指定字型名稱。 此字串的長度不得超過 30 個字元。 Windows [EnumFont 家庭](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw)函數可用於枚舉所有當前可用的字體。 如果*lpszFace 名稱*為 NULL,則 GDI 使用與設備無關的字體。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

隨後可以選擇該字體作為任何設備上下文的字體。

該`CreateFont`功能不會創建新的 Windows GDI 字體。 它只是從 GDI 可用的物理字體中選擇最接近的匹配項。

在創建邏輯字體時,應用程式可以使用大多數參數的預設設置。 應將指定特定值的參數為*nHeight*和*lpszFace 名稱*。 如果應用程式未設置*nHeight*和*lpszFace 名稱*,則創建的邏輯字體與設備相關。

完成`CFont``CreateFont`函數創建的物件後,使用`CDC::SelectObject`在設備上下文中選擇其他字體,然後刪除不再`CFont`需要的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

## <a name="cfontcreatefontindirect"></a><a name="createfontindirect"></a>CFont::創建字體間接

初始化具有`CFont` [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構中給出的特徵的物件。

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>參數

*lpLogFont*<br/>
指向定義邏輯`LOGFONT`字體特徵的結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

隨後可以選擇該字體作為任何設備的當前字體。

此字體具有[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構中指定的特徵。 使用[CDC::選擇物件](../../mfc/reference/cdc-class.md#selectobject)成員函數選擇字體時,GDI 字體映射器會嘗試將邏輯字體與現有物理字型匹配。 如果字體映射器找不到邏輯字體的精確匹配,則提供具有其特徵與盡可能多的請求特徵匹配的替代字體。

`CFont`當您不再需要`CreateFontIndirect`函數創建的物件時,請`CDC::SelectObject`使用 在設備上下文中選擇其他字體,然後刪除`CFont`不再需要的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

## <a name="cfontcreatepointfont"></a><a name="createpointfont"></a>CFont::建立點字型

此功能提供了創建指定字體和點大小的字型的簡單方法。

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>參數

*n點大*<br/>
請求的字體高度(以點十分之一表示)。 (例如,通過 120 請求 12 點字體。

*lpszFace 名稱*<br/>
指向`CString`null 連接端的字串的或指標,該字串指定字型名稱。 此字串的長度不得超過 30 個字元。 Windows 'EnumFont 家庭函數可用於枚舉所有當前可用的字體。 如果*lpszFaceName*為 NULL,則 GDI 使用與設備無關的字體。

*pDC*<br/>
指向用於以*nPointSize*為單位的高度轉換為邏輯單位的[CDC](../../mfc/reference/cdc-class.md)物件。 如果為 NULL,則轉換時將使用螢幕裝置上下文。

### <a name="return-value"></a>傳回值

如果成功,則非零,否則為 0。

### <a name="remarks"></a>備註

它使用*pDC*指向的 CDC 物件,自動將*nPointSize 的高度*轉換為邏輯單位。

完成`CFont``CreatePointFont`函數創建的物件後,首先從設備上下文中選擇字體,然後`CFont`刪除 該物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

## <a name="cfontcreatepointfontindirect"></a><a name="createpointfontindirect"></a>CFont::創建點字體間接

此函數與[CreateFont 間接函數](#createfontindirect)相同`lfHeight`,`LOGFONT`只不過的成員 以點的十分之一而不是設備單位進行解釋。

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>參數

*lpLogFont*<br/>
指向定義邏輯字體特徵的[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構。 `LOGFONT`結構`lfHeight`的成員以點的十分之一而不是邏輯單位來衡量。 (例如,設置為`lfHeight`120 以請求 12 點字體。

*pDC*<br/>
指向用於將[CDC](../../mfc/reference/cdc-class.md)高度`lfHeight`轉換為邏輯單位的CDC物件。 如果為 NULL,則轉換時將使用螢幕裝置上下文。

### <a name="return-value"></a>傳回值

如果成功,則非零,否則為 0。

### <a name="remarks"></a>備註

在將`LOGFONT`結構傳遞到 Windows`lfHeight`之前 ,此功能使用*pDC*指向的 CDC 物件自動將 高度轉換為邏輯單位。

完成`CFont``CreatePointFontIndirect`函數創建的物件後,首先從設備上下文中選擇字體,然後`CFont`刪除 該物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

## <a name="cfontfromhandle"></a><a name="fromhandle"></a>CFont::從手柄

當為 Windows `CFont` GDI 字體物件提供 HFONT 句柄時,傳回指向物件的指標。

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>參數

*h字型*<br/>
Windows 字體的 HFONT 句柄。

### <a name="return-value"></a>傳回值

指向`CFont`物件的指標(如果成功);如果成功,則指向物件。否則 NULL。

### <a name="remarks"></a>備註

如果物件`CFont`尚未附加到句柄,則創建並附加`CFont`臨時 物件。 此臨時`CFont`物件僅在下次應用程式在其事件迴圈中有空閑時間之前有效,此時將刪除所有臨時圖形物件。 另一種說法是臨時物件僅在處理一個視窗消息時有效。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

## <a name="cfontgetlogfont"></a><a name="getlogfont"></a>CFont::取得紀錄字型

調用此函數以檢索`LOGFONT``CFont`的結構副本。

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>參數

*pLogFont*<br/>
指向[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)結構以接收字體資訊。

### <a name="return-value"></a>傳回值

如果函數成功,則非零,否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

## <a name="cfontoperator-hfont"></a><a name="operator_hfont"></a>CFont::操作員惠普

使用此運算元獲取附加到`CFont`物件的字型的 Windows GDI 句柄。

```
operator HFONT() const;
```

### <a name="return-value"></a>傳回值

`CFont`附加到的 Windows GDI 字體物件的句柄(如果成功);否則 NULL。

### <a name="remarks"></a>備註

由於此運算符自動用於從`CFont`[字型和文字](/windows/win32/gdi/fonts-and-text)轉換,因此您可以將物件傳遞給`CFont`預期 HFONT 的函數。

有關使用圖形物件的詳細資訊,請參閱 Windows SDK 中的[圖形物件](/windows/win32/gdi/graphic-objects)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
