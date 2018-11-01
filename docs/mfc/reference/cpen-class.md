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
ms.openlocfilehash: dc9216d10b620a79aa8e20e240791207f25a65c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531556"
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
|[CPen::CPen](#cpen)|建構 `CPen` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPen::CreatePen](#createpen)|使用指定的樣式、 寬度和筆刷屬性中建立邏輯的外觀或幾何畫筆，並將它附加至`CPen`物件。|
|[CPen::CreatePenIndirect](#createpenindirect)|使用樣式、 寬度和色彩提供建立畫筆[LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)結構，並將它附加至`CPen`物件。|
|[CPen::FromHandle](#fromhandle)|將指標傳回至`CPen`物件時指定 Windows HPEN。|
|[CPen::GetExtLogPen](#getextlogpen)|取得[EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen)基礎結構。|
|[CPen::GetLogPen](#getlogpen)|取得[LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)基礎結構。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CPen::operator HPEN](#operator_hpen)|傳回附加至的 Windows 控制代碼`CPen`物件。|

## <a name="remarks"></a>備註

如需有關使用`CPen`，請參閱 <<c2> [ 圖形物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cpen"></a>  CPen::CPen

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
指定的畫筆樣式。 建構函式的第一個版本中的這個參數可以是下列值之一：

- PS_SOLID 建立穩固的畫筆。

- PS_DASH 建立虛線的畫筆。 只有在畫筆寬度為 1 或更少，在裝置中的單位時，才有效。

- PS_DOT 建立虛線的畫筆。 只有在畫筆寬度為 1 或更少，在裝置中的單位時，才有效。

- PS_DASHDOT 建立畫筆交替的虛線和點。 只有在畫筆寬度為 1 或更少，在裝置中的單位時，才有效。

- PS_DASHDOTDOT 建立的畫筆交替的虛線和 double 的點。 只有在畫筆寬度為 1 或更少，在裝置中的單位時，才有效。

- PS_NULL 會建立為 null 的畫筆。

- PS_INSIDEFRAME 建立畫筆繪製線條封閉形狀的框架內，產生 Windows GDI 輸出指定的週框的函式 (例如`Ellipse`， `Rectangle`， `RoundRect`， `Pie`，並`Chord`成員函式)。 此樣式時搭配 Windows GDI 輸出函式未指定的週框 (比方說，`LineTo`成員函式)，將畫筆繪圖區域不受限於一個框架。

第二版`CPen`建構函式指定的型別、 樣式、 結束端點和聯結屬性組合。 每個類別目錄中的值應結合使用位元的 OR 運算子 (&#124;)。 畫筆類型可以是下列值之一：

- PS_GEOMETRIC 建立幾何的畫筆。

- PS_COSMETIC 建立外觀的畫筆。

   第二版`CPen`建構函式新增下列畫筆樣式*nPenStyle*:

- PS_ALTERNATE 建立畫筆設定每個像素。 （此樣式是只適用於表面的畫筆的）。

- 使用樣式陣列畫筆 PS_USERSTYLE 建立的使用者所提供。

   結束端點可以是下列值之一：

- PS_ENDCAP_ROUND 末尾會捨入。

- PS_ENDCAP_SQUARE 末尾是正方形。

- PS_ENDCAP_FLAT 末尾是平面的。

   聯結可以是下列值之一：

- 被斜角 PS_JOIN_BEVEL 聯結。

- PS_JOIN_MITER 聯結是斜接內所設定的目前限制時，它們[SetMiterLimit](/windows/desktop/api/wingdi/nf-wingdi-setmiterlimit)函式。 如果聯結超出此限制，它被斜角。

- PS_JOIN_ROUND 聯結會捨入。

*nWidth*<br/>
指定畫筆的寬度。

- 建構函式的第一個版本，如果此值為 0，以裝置為單位的寬度一律是 1 個像素，不論對應模式。

- 第二個版本的建構函式，如果*nPenStyle*是 PS_GEOMETRIC，寬度有以邏輯單位表示。 如果*nPenStyle*是 PS_COSMETIC，寬度必須設定為 1。

*crColor*<br/>
包含畫筆的 RGB 色彩。

*pLogBrush*<br/>
指向`LOGBRUSH`結構。 如果*nPenStyle*是 PS_COSMETIC， *lbColor*的成員`LOGBRUSH`結構指定的畫筆色彩和*lbStyle*成員`LOGBRUSH`結構，必須設定 BS_SOLID。 如果*nPenStyle*是 PS_GEOMETRIC，所有成員必須都用來指定畫筆的筆刷屬性。

*nStyleCount*<br/>
指定的長度，單位 doubleword *lpStyle*陣列。 此值必須是零，如果*nPenStyle*不 PS_USERSTYLE。

*lpStyle*<br/>
指向陣列的 doubleword 值。 第一個值指定使用者定義的樣式中的第一條虛線的長度，第二個值指定長度的第一個空格，依此類推。 這個指標必須是 NULL，如果*nPenStyle*不 PS_USERSTYLE。

### <a name="remarks"></a>備註

如果您使用建構函式沒有引數時，您必須初始化產生`CPen`物件`CreatePen`， `CreatePenIndirect`，或`CreateStockObject`成員函式。

如果您使用引數的建構函式，則不不需要任何進一步的初始化。 如果發生錯誤，而不使用引數的建構函式一定會成功，則引數的建構函式會擲回例外狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

##  <a name="createpen"></a>  CPen::CreatePen

使用指定的樣式、 寬度和筆刷屬性中建立邏輯的外觀或幾何畫筆，並將它附加至`CPen`物件。

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
指定樣式的畫筆。 如需可能值的清單，請參閱 < *nPenStyle*中的參數[CPen](#cpen)建構函式。

*nWidth*<br/>
指定畫筆的寬度。

- 第一個版本的`CreatePen`，如果此值為 0，以裝置為單位的寬度永遠是 1 個像素，不論對應模式。

- 第二個版本的`CreatePen`的話*nPenStyle*是 PS_GEOMETRIC，寬度有以邏輯單位表示。 如果*nPenStyle*是 PS_COSMETIC，寬度必須設定為 1。

*crColor*<br/>
包含畫筆的 RGB 色彩。

*pLogBrush*<br/>
指向[LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush)結構。 如果*nPenStyle*是 PS_COSMETIC，`lbColor`隸屬`LOGBRUSH`結構指定的畫筆色彩和*lbStyle*隸屬`LOGBRUSH`結構必須設為 BS_純色。 如果 nPenStyle PS_GEOMETRIC，所有成員必須都用於指定畫筆的筆刷屬性。

*nStyleCount*<br/>
指定的長度，單位 doubleword *lpStyle*陣列。 此值必須是零，如果*nPenStyle*不 PS_USERSTYLE。

*lpStyle*<br/>
指向陣列的 doubleword 值。 第一個值指定使用者定義的樣式中的第一條虛線的長度，第二個值指定長度的第一個空格，依此類推。 這個指標必須是 NULL，如果*nPenStyle*不 PS_USERSTYLE。

### <a name="return-value"></a>傳回值

如果成功，為非零，如果方法失敗。

### <a name="remarks"></a>備註

第一版`CreatePen`初始化使用指定的樣式、 寬度和色彩的畫筆。 畫筆可以接著選取作為目前的畫筆，為任何裝置內容。

具有寬度大於 1 個像素，應一律具有 PS_NULL、 PS_SOLID，或是 PS_INSIDEFRAME 樣式的畫筆。

如果畫筆 PS_INSIDEFRAME 樣式和色彩的不符合，邏輯的色彩表中的色彩，畫筆會繪製遞色色彩。 PS_SOLID 畫筆樣式無法用於建立以遞色色彩的畫筆。 樣式 PS_INSIDEFRAME 等同於 PS_SOLID 畫筆寬度是否小於或等於 1。

第二版`CreatePen`初始化具有指定的樣式、 寬度和筆刷屬性邏輯表面或幾何畫筆。 表面畫筆的寬度永遠為 1;以全局單位一律指定幾何的畫筆的寬度。 應用程式建立邏輯的畫筆之後，它可以藉由呼叫放入裝置內容中選取該畫筆[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)函式。 畫筆選入裝置內容之後，它可用來繪製的直線和曲線。

- 如果*nPenStyle*且 PS_COSMETIC PS_USERSTYLE 中的項目*lpStyle*陣列指定虛線和間距的長度，單位為樣式。 樣式單位是由以畫筆用來繪製一條線的裝置定義。

- 如果*nPenStyle*且 PS_GEOMETRIC PS_USERSTYLE 中的項目*lpStyle*陣列指定虛線和間距的長度，以邏輯單位表示。

- 如果*nPenStyle*是 PS_ALTERNATE 樣式單位會被忽略，設定每個像素。

當應用程式不再需要給定的畫筆時，它應該呼叫[CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函式或終結`CPen`物件，以便資源已不存在於使用。 選取裝置內容中的畫筆時，應用程式不應刪除畫筆。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

##  <a name="createpenindirect"></a>  CPen::CreatePenIndirect

初始化具有樣式、 寬度和色彩所指向的結構所提供的畫筆*lpLogPen*。

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>參數

*lpLogPen*<br/>
Windows 會指向[LOGPEN](../../mfc/reference/logpen-structure.md)包含畫筆的相關資訊的結構。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

具有寬度大於 1 個像素，應一律具有 PS_NULL、 PS_SOLID，或是 PS_INSIDEFRAME 樣式的畫筆。

如果畫筆 PS_INSIDEFRAME 樣式和色彩的不符合，邏輯的色彩表中的色彩，畫筆會繪製遞色色彩。 畫筆寬度小於或等於 1 時，等於 PS_SOLID PS_INSIDEFRAME 樣式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

##  <a name="fromhandle"></a>  CPen::FromHandle

將指標傳回至`CPen`物件控制代碼提供 Windows GDI pen 物件。

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>參數

*hPen*<br/>
`HPEN` Windows GDI 畫筆的控制代碼。

### <a name="return-value"></a>傳回值

指標`CPen`如果成功，否則為 NULL 的物件。

### <a name="remarks"></a>備註

如果 `CPen` 物件沒有附加至控制代碼，會建立並附加暫存 `CPen` 物件。 此暫存`CPen`物件是否有效，直到下一次應用程式在其事件迴圈中有閒置的時間，在那所有暫存的圖形物件，會刪除只。 換句話說，暫存的物件才有效期間的一個視窗訊息處理。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

##  <a name="getextlogpen"></a>  CPen::GetExtLogPen

取得`EXTLOGPEN`基礎結構。

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>參數

*pLogPen*<br/>
指向[EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen)包含畫筆的相關資訊的結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`EXTLOGPEN`結構會定義樣式、 寬度和畫筆的筆刷屬性。 例如，呼叫`GetExtLogPen`以符合特定樣式的畫筆。

請參閱 Windows sdk for pen 屬性的相關資訊的下列主題：

- [GetObject](/windows/desktop/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/desktop/api/wingdi/ns-wingdi-tagextlogpen)

- [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)

- [ExtCreatePen](/windows/desktop/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>範例

下列程式碼範例示範如何呼叫`GetExtLogPen`擷取手寫筆的屬性，並接著使用相同的色彩建立新的表面的畫筆。

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

##  <a name="getlogpen"></a>  CPen::GetLogPen

取得`LOGPEN`基礎結構。

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>參數

*pLogPen*<br/>
指向[LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)結構以包含畫筆的相關資訊。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`LOGPEN`結構會定義樣式、 色彩和畫筆的模式。

例如，呼叫`GetLogPen`以符合特定樣式的畫筆。

請參閱 Windows sdk for pen 屬性的相關資訊的下列主題：

- [GetObject](/windows/desktop/api/wingdi/nf-wingdi-getobject)

- [LOGPEN](/windows/desktop/api/wingdi/ns-wingdi-taglogpen)

### <a name="example"></a>範例

下列程式碼範例示範如何呼叫`GetLogPen`擷取畫筆字元，並再建立新的實心筆相同的色彩。

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

##  <a name="operator_hpen"></a>  CPen::operator HPEN

取得附加的 Windows GDI 控制代碼的`CPen`物件。

```
operator HPEN() const;
```

### <a name="return-value"></a>傳回值

如果成功，Windows GDI 物件的控制代碼所表示`CPen`物件; 否則為 NULL。

### <a name="remarks"></a>備註

這位操作員便轉型運算子，可支援直接使用 HPEN 物件。

如需有關如何使用 圖形物件的詳細資訊，請參閱[圖形物件](/windows/desktop/gdi/graphic-objects)Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CBrush 類別](../../mfc/reference/cbrush-class.md)
