---
title: CPen 類別
ms.date: 11/04/2016
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
ms.openlocfilehash: 952d270acd47b5834a06b731f7875ea2efdd4695
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502944"
---
# <a name="cpen-class"></a>CPen 類別

封裝 Windows 繪圖裝置介面 (GDI) 畫筆。

## <a name="syntax"></a>語法

```
class CPen : public CGdiObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CPen:: CPen](#cpen)|建構 `CPen` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPen::CreatePen](#createpen)|使用指定的樣式、寬度和筆刷屬性, 建立邏輯表面或幾何畫筆, 並將其附加至`CPen`物件。|
|[CPen::CreatePenIndirect](#createpenindirect)|使用[LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)結構中提供的樣式、寬度和色彩來建立畫筆, 並將其附加至`CPen`物件。|
|[CPen::FromHandle](#fromhandle)|當給定 Windows HPEN 時`CPen` , 傳回物件的指標。|
|[CPen::GetExtLogPen](#getextlogpen)|取得[EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)的基礎結構。|
|[CPen::GetLogPen](#getlogpen)|取得[LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)的基礎結構。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CPen:: operator HPEN](#operator_hpen)|傳回附加至`CPen`物件的 Windows 控制碼。|

## <a name="remarks"></a>備註

如需使用`CPen`的詳細資訊, 請參閱[繪圖物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cpen"></a>CPen:: CPen

建構 `CPen` 物件。

```
CPen();

CPen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

CPen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>參數

*nPenStyle*<br/>
指定畫筆樣式。 第一個版本的函式中的這個參數可以是下列其中一個值:

- PS_SOLID 會建立實心畫筆。

- PS_DASH 會建立虛線畫筆。 只有當畫筆寬度為1或小於 (以裝置為單位) 時才有效。

- PS_DOT 會建立虛線畫筆。 只有當畫筆寬度為1或小於 (以裝置為單位) 時才有效。

- PS_DASHDOT 會建立具有交替破折號和點的畫筆。 只有當畫筆寬度為1或小於 (以裝置為單位) 時才有效。

- PS_DASHDOTDOT 會建立具有交替破折號和雙點的畫筆。 只有當畫筆寬度為1或小於 (以裝置為單位) 時才有效。

- PS_Null 會建立 Null 畫筆。

- PS_INSIDEFRAME 會建立一個畫筆, 它會在指定周框矩形的 Windows GDI 輸出函式所產生的封閉圖形框架`Ellipse`內繪製線條 ( `Rectangle` `RoundRect` `Pie`例如,、、、和`Chord`成員函式)。 當此樣式與未指定周框矩形的 Windows GDI 輸出函式 ( `LineTo`例如成員函式) 搭配使用時, 畫筆的繪圖區域不會受到框架的限制。

第二個版本的`CPen`函式會指定類型、樣式、結束端點和聯結屬性的組合。 每個類別目錄的值都應該使用位 OR 運算子 (&#124;) 結合。 畫筆類型可以是下列其中一個值:

- PS_GEOMETRIC 會建立幾何畫筆。

- PS_COSMETIC 會建立裝飾畫筆。

   第二個版本的`CPen`函式會為*nPenStyle*新增下列畫筆樣式:

- PS_ALTERNATE 會建立可設定每個其他圖元的畫筆。 (此樣式僅適用于裝飾畫筆)。

- PS_USERSTYLE 會建立一個使用使用者所提供之樣式陣列的畫筆。

   結尾上限可以是下列其中一個值:

- PS_ENDCAP_ROUND 結束上限為 ROUND。

- PS_ENDCAP_SQUARE 結束上限為方形。

- PS_ENDCAP_FLAT 結束上限是平面的。

   聯結可以是下列其中一個值:

- PS_JOIN_BEVEL 聯結是斜切的。

- 當 PS_JOIN_MITER 聯結在[SetMiterLimit](/windows/win32/api/wingdi/nf-wingdi-setmiterlimit)函式所設定的目前限制範圍內時, 會進行斜接。 如果聯結超過此限制, 則為「斜切」。

- PS_JOIN_ROUND 聯結是 ROUND 的。

*nWidth*<br/>
指定畫筆的寬度。

- 針對第一個版本的函式, 如果此值為 0, 則不論對應模式為何, 裝置單位的寬度一律為1個圖元。

- 針對第二個版本的函式, 如果*nPenStyle*為 PS_GEOMETRIC, 則會以邏輯單元指定寬度。 如果*nPenStyle*為 PS_COSMETIC, 則寬度必須設定為1。

*crColor*<br/>
包含畫筆的 RGB 色彩。

*pLogBrush*<br/>
`LOGBRUSH`指向結構。 如果*nPenStyle*是 PS_COSMETIC, 則 `LOGBRUSH`結構的 lbColor 成員會指定畫筆的色彩, `LOGBRUSH`而結構的*lbStyle*成員必須設定為 BS_SOLID。 如果*nPenStyle*為 PS_GEOMETRIC, 則所有成員都必須用來指定畫筆的筆刷屬性。

*nStyleCount*<br/>
指定*lpStyle*陣列的長度 (以長時間單位表示)。 如果*nPenStyle*不是 PS_USERSTYLE, 這個值必須是零。

*lpStyle*<br/>
指向雙量值的陣列。 第一個值會指定使用者定義樣式中第一個虛線的長度, 第二個值指定第一個空格的長度, 依此類推。 如果*nPenStyle*不是 PS_USERSTYLE, 這個指標必須是 Null。

### <a name="remarks"></a>備註

如果您使用不含引數的函式, 則必須使用`CPen` `CreatePen`、 `CreatePenIndirect`或`CreateStockObject`成員函式來初始化產生的物件。

如果您使用接受引數的函數, 則不需要進一步的初始化。 如果遇到錯誤, 含有引數的函式可能會擲回例外狀況, 而不含引數的函式一律會成功。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

##  <a name="createpen"></a>CPen:: CreatePen

使用指定的樣式、寬度和筆刷屬性, 建立邏輯表面或幾何畫筆, 並將其附加至`CPen`物件。

```
BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>參數

*nPenStyle*<br/>
指定畫筆的樣式。 如需可能值的清單, 請參閱[CPen](#cpen)函數中的*nPenStyle*參數。

*nWidth*<br/>
指定畫筆的寬度。

- 若為第一個版本`CreatePen`的, 如果此值為 0, 則不論對應模式為何, 裝置單位的寬度一律為1個圖元。

- 針對第二個版本`CreatePen`的, 如果*nPenStyle*為 PS_GEOMETRIC, 則會以邏輯單元指定寬度。 如果*nPenStyle*為 PS_COSMETIC, 則寬度必須設定為1。

*crColor*<br/>
包含畫筆的 RGB 色彩。

*pLogBrush*<br/>
指向[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)結構。 如果*nPenStyle*為 PS_COSMETIC, `lbColor`則`LOGBRUSH`結構的成員會指定`LOGBRUSH`畫筆的色彩, 而結構的*lbStyle*成員則必須設定為 BS_SOLID。 如果 nPenStyle 為 PS_GEOMETRIC, 則所有成員都必須用來指定畫筆的筆刷屬性。

*nStyleCount*<br/>
指定*lpStyle*陣列的長度 (以長時間單位表示)。 如果*nPenStyle*不是 PS_USERSTYLE, 這個值必須是零。

*lpStyle*<br/>
指向雙量值的陣列。 第一個值會指定使用者定義樣式中第一個虛線的長度, 第二個值指定第一個空格的長度, 依此類推。 如果*nPenStyle*不是 PS_USERSTYLE, 這個指標必須是 Null。

### <a name="return-value"></a>傳回值

如果成功, 則為非零, 如果方法失敗, 則為零。

### <a name="remarks"></a>備註

第一個版本會`CreatePen`使用指定的樣式、寬度和色彩來初始化畫筆。 接著, 您可以將畫筆選取為任何裝置內容的目前畫筆。

寬度大於1圖元的畫筆一定要有 PS_Null、PS_SOLID 或 PS_INSIDEFRAME 樣式。

如果畫筆的 PS_INSIDEFRAME 樣式和色彩與邏輯色彩表中的色彩不相符, 就會以遞色繪製畫筆。 PS_SOLID 畫筆樣式無法用來建立具有遞色色彩的畫筆。 如果畫筆寬度小於或等於 1, 則樣式 PS_INSIDEFRAME 與 PS_SOLID 相同。

的第二個`CreatePen`版本會初始化具有指定的樣式、寬度和筆刷屬性的邏輯表面或幾何畫筆。 表面畫筆的寬度一律為 1;幾何畫筆的寬度一律是以世界單位來指定。 在應用程式建立邏輯畫筆之後, 它可以藉由呼叫[CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject)函式, 將該畫筆選取到裝置內容中。 將畫筆選取到裝置內容之後, 就可以用來繪製線條和曲線。

- 如果*nPenStyle*為 PS_COSMETIC 和 PS_USERSTYLE, 則*lpStyle*陣列中的專案會在樣式單位中指定虛線和空格的長度。 樣式單位是由畫筆用來繪製線條的裝置所定義。

- 如果*nPenStyle*為 PS_GEOMETRIC 和 PS_USERSTYLE, 則*lpStyle*陣列中的專案會以邏輯單元指定破折號和空格的長度。

- 如果*nPenStyle*為 PS_ALTERNATE, 則會忽略樣式單位, 並設定其他每個圖元。

當應用程式不再需要指定的畫筆時, 它應該呼叫[CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式, 或`CPen`終結物件, 使資源不再使用。 在裝置內容中選取畫筆時, 應用程式不應該刪除畫筆。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

##  <a name="createpenindirect"></a>CPen:: CreatePenIndirect

初始化畫筆, 其具有在*lpLogPen*所指向的結構中提供的樣式、寬度和色彩。

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>參數

*lpLogPen*<br/>
指向包含畫筆相關資訊的 Windows [LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)結構。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

寬度大於1圖元的畫筆一定要有 PS_Null、PS_SOLID 或 PS_INSIDEFRAME 樣式。

如果畫筆的 PS_INSIDEFRAME 樣式和色彩與邏輯色彩表中的色彩不相符, 就會以遞色繪製畫筆。 如果畫筆寬度小於或等於 1, 則 PS_INSIDEFRAME 樣式與 PS_SOLID 相同。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

##  <a name="fromhandle"></a>CPen:: FromHandle

傳回`CPen`物件的指標, 指定 Windows GDI 畫筆物件的控制碼。

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>參數

*hPen*<br/>
`HPEN`Windows GDI 畫筆的控制碼。

### <a name="return-value"></a>傳回值

如果成功, 則`CPen`為物件的指標; 否則為 Null。

### <a name="remarks"></a>備註

如果 `CPen` 物件沒有附加至控制代碼，會建立並附加暫存 `CPen` 物件。 這個暫存`CPen`物件只有在下一次應用程式的事件迴圈中有閒置時間時才有效, 此時所有的暫存繪圖物件都會被刪除。 換句話說, 暫存物件只在處理一個視窗訊息期間有效。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

##  <a name="getextlogpen"></a>CPen:: GetExtLogPen

`EXTLOGPEN`取得基礎結構。

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>參數

*pLogPen*<br/>
指向包含畫筆相關資訊的[EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`EXTLOGPEN`結構會定義畫筆的樣式、寬度和筆刷屬性。 例如, 呼叫`GetExtLogPen`以符合畫筆的特定樣式。

如需畫筆屬性的相關資訊, 請參閱 Windows SDK 中的下列主題:

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

- [ExtCreatePen](/windows/win32/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>範例

下列程式碼範例將示範`GetExtLogPen`如何呼叫來抓取畫筆的屬性, 然後使用相同的色彩建立新的表面畫筆。

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

##  <a name="getlogpen"></a>  CPen::GetLogPen

`LOGPEN`取得基礎結構。

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>參數

*pLogPen*<br/>
指向包含畫筆相關資訊的[LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`LOGPEN`結構會定義畫筆的樣式、色彩和模式。

例如, 呼叫`GetLogPen`以符合特定的畫筆樣式。

如需畫筆屬性的相關資訊, 請參閱 Windows SDK 中的下列主題:

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

### <a name="example"></a>範例

下列程式碼範例將示範`GetLogPen`如何呼叫來抓取畫筆字元, 然後使用相同的色彩建立新的單色筆刷。

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

##  <a name="operator_hpen"></a>CPen:: operator HPEN

取得`CPen`物件附加的 Windows GDI 控制碼。

```
operator HPEN() const;
```

### <a name="return-value"></a>傳回值

如果成功, 則為`CPen`物件所表示之 Windows GDI 物件的控制碼, 否則為 Null。

### <a name="remarks"></a>備註

這個運算子是一個轉型運算子, 可支援直接使用 HPEN 物件。

如需使用繪圖物件的詳細資訊, 請參閱 Windows SDK 中的[繪圖物件](/windows/win32/gdi/graphic-objects)一文。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CBrush 類別](../../mfc/reference/cbrush-class.md)
