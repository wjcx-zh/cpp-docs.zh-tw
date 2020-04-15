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
ms.openlocfilehash: e15dc53fafa0d80f1b52b3fe77f3635c592a4346
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364074"
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
|[CPen:CPen](#cpen)|建構 `CPen` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CPen::創建筆](#createpen)|創建具有指定樣式、寬度和畫筆屬性的邏輯修飾筆或幾何筆,並將其附加到`CPen`物件。|
|[CPen:創建間接](#createpenindirect)|創建具有[LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)結構中給定的樣式、寬度和顏色的筆,並將其`CPen`附加到 物件。|
|[CPen:從手柄](#fromhandle)|在給定 Windows `CPen` HPEN 時返回指向物件的指標。|
|[CPen:獲取ExtLogPen](#getextlogpen)|獲取[EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)基礎結構。|
|[CPen:獲取LogPen](#getlogpen)|獲取[LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)基礎結構。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CPen::操作員 HPEN](#operator_hpen)|返回附加到`CPen`物件的 Windows 句柄。|

## <a name="remarks"></a>備註

有關`CPen`使用的詳細資訊,請參考[圖形物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cpencpen"></a><a name="cpen"></a>CPen:CPen

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
指定筆樣式。 建構函數的第一版本中的此參數可以是以下值之一:

- PS_SOLID 創建實心筆。

- PS_DASH創建虛線筆。 僅當筆寬度為 1 或更少時(以設備單位為單位)才有效。

- PS_DOT創建虛筆。 僅當筆寬度為 1 或更少時(以設備單位為單位)才有效。

- PS_DASHDOT創建具有交替破折號和點的筆。 僅當筆寬度為 1 或更少時(以設備單位為單位)才有效。

- PS_DASHDOTDOT創建具有交替破折號和雙點的筆。 僅當筆寬度為 1 或更少時(以設備單位為單位)才有效。

- PS_NULL創建空筆。

- PS_INSIDEFRAME 創建一個筆,在 Windows GDI`Ellipse`輸出函數`Rectangle``RoundRect`(`Pie``Chord`例如, 、 、 和成員函數) 生成的封閉形狀框架內繪製一條線。 當此樣式與不指定邊界矩形(例如`LineTo`成員函數)的 Windows GDI 輸出函數一起使用時,筆的繪圖區域不受框架的限制。

建構函數的第`CPen`二個版本指定類型、樣式、結束上限和聯接屬性的組合。 每個類別中的值應使用位或運算符 (&#124;)進行組合。 筆型態可以是以下值之一:

- PS_GEOMETRIC創建幾何筆。

- PS_COSMETIC創建一個化妝筆。

   建構函數的第`CPen`二個版本為*nPenStyle*新增了以下筆樣式 :

- PS_ALTERNATE 創建一個可設置其他像素的筆。 (此樣式僅適用於化妝筆。

- PS_USERSTYLE 創建使用使用者提供的樣式陣列的筆。

   端蓋可以是以下值之一:

- PS_ENDCAP_ROUND端蓋是圓形的。

- PS_ENDCAP_SQUARE端蓋是方形的。

- PS_ENDCAP_FLAT端蓋是平的。

   聯接可以是以下值之一:

- PS_JOIN_BEVEL聯接是被否決的。

- PS_JOIN_MITER聯接在[SetMiter Limit](/windows/win32/api/wingdi/nf-wingdi-setmiterlimit)函數設置的當前限制內時,將小入。 如果聯接超過此限制,則將其所仿。

- PS_JOIN_ROUND聯接是圓的。

*n 寬度*<br/>
指定筆的寬度。

- 對於構造函數的第一個版本,如果此值為 0,則無論映射模式如何,設備單位的寬度始終為 1 圖元。

- 對於構造函數的第二個版本,如果*nPenStyle* PS_GEOMETRIC,則寬度以邏輯單位表示。 如果*nPenStyle* PS_COSMETIC,則必須將寬度設置為 1。

*crColor*<br/>
包含筆的 RGB 顏色。

*pLogBrush*<br/>
指向結構`LOGBRUSH`。 如果*nPenStyle*是`LOGBRUSH`PS_COSMETIC, 則結構的*lbColor*成員指定筆的顏色,`LOGBRUSH`並且必須將結構的*lbStyle*成員設置為BS_SOLID。 如果*nPenStyle* PS_GEOMETRIC,則必須使用所有成員指定筆的畫筆屬性。

*n 樣式計數*<br/>
指定*lpStyle*陣列的長度(以雙字單位為單位)。 如果*nPenStyle*不是PS_USERSTYLE,則此值必須為零。

*lpStyle*<br/>
指向雙字值陣列。 第一個值指定用戶定義樣式中第一個虛線的長度,第二個值指定第一個空格的長度,等等。 如果未PS_USERSTYLE *nPenStyle,* 則此指標必須為 NULL。

### <a name="remarks"></a>備註

如果使用沒有參數的建構函數,`CPen`則必須`CreatePen`使用 初始化生成的`CreatePenIndirect`物件`CreateStockObject`, 或成員函數。

如果使用採用參數的構造函數,則無需進一步初始化。 如果遇到錯誤,帶參數的構造函數可以引發異常,而沒有參數的構造函數將始終成功。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

## <a name="cpencreatepen"></a><a name="createpen"></a>CPen::創建筆

創建具有指定樣式、寬度和畫筆屬性的邏輯修飾筆或幾何筆,並將其附加到`CPen`物件。

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
指定筆的樣式。 有關可能值的清單,請參閱[CPen](#cpen)構造函數中的*nPenStyle*參數。

*n 寬度*<br/>
指定筆的寬度。

- 對於的第一個版本`CreatePen`,如果此值為 0,則無論映射模式如何,設備單位的寬度始終為 1 圖元。

- 對於的第二個版本`CreatePen`,如果*nPenStylePS_GEOMETRIC,* 則寬度以邏輯單位表示。 如果*nPenStyle* PS_COSMETIC,則必須將寬度設置為 1。

*crColor*<br/>
包含筆的 RGB 顏色。

*pLogBrush*<br/>
指向[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)結構。 如果*nPenStyle* `lbColor``LOGBRUSH`PS_COSMETIC, 則結構成員指定筆的顏色,並且必須`LOGBRUSH`將結構的*lbStyle*成員設置為BS_SOLID。 如果 nPenStyle PS_GEOMETRIC,則必須使用所有成員指定筆的畫筆屬性。

*n 樣式計數*<br/>
指定*lpStyle*陣列的長度(以雙字單位為單位)。 如果*nPenStyle*不是PS_USERSTYLE,則此值必須為零。

*lpStyle*<br/>
指向雙字值陣列。 第一個值指定用戶定義樣式中第一個虛線的長度,第二個值指定第一個空格的長度,等等。 如果未PS_USERSTYLE *nPenStyle,* 則此指標必須為 NULL。

### <a name="return-value"></a>傳回值

如果成功,則為非零;如果方法失敗,則為零。

### <a name="remarks"></a>備註

第一個版本的初始`CreatePen`化具有指定樣式、寬度和顏色的筆。 隨後,可以為任何設備上下文選擇筆作為當前筆。

寬度大於 1 像素的筆應始終具有PS_NULL、PS_SOLID或PS_INSIDEFRAME樣式。

如果筆具有PS_INSIDEFRAME樣式和與邏輯顏色表中的顏色不匹配的顏色,則筆將繪製為抖紅色。 PS_SOLID筆樣式不能用於創建具有抖紅色的筆。 如果筆寬度小於或等於 1,則樣式PS_INSIDEFRAME與PS_SOLID相同。

第二個版本的初始`CreatePen`化邏輯修飾筆或幾何筆具有指定的樣式、寬度和畫筆屬性。 化妝筆的寬度始終為 1;幾何筆的寬度始終以世界單位指定。 應用程式創建邏輯筆後,可以透過調用[CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)函數選擇該筆到設備上下文中。 將筆選擇到設備上下文中后,它可用於繪製線條和曲線。

- 如果*nPenStyle* PS_COSMETIC和PS_USERSTYLE,*則 lpStyle*陣列中的條目以樣式單位指定破折號和空格的長度。 樣式單元由筆用於繪製線條的設備定義。

- 如果*nPenStyle*是PS_GEOMETRIC和PS_USERSTYLE,則*lpStyle*陣列中的條目以邏輯單位指定破折號和空格的長度。

- 如果*nPenStyle* PS_ALTERNATE,則忽略樣式單元,並設置所有其他圖元。

當應用程式不再需要給定的筆時,它應該調用[CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)成員函數或`CPen`銷毀 物件,以便資源不再使用。 在設備上下文中選擇筆時,應用程式不應刪除筆。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

## <a name="cpencreatepenindirect"></a><a name="createpenindirect"></a>CPen:創建間接

初始化具有*lpLogPen*指向的結構中給出的樣式、寬度和顏色的筆。

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>參數

*lpLogPen*<br/>
指向包含筆資訊的 Windows [LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)結構。

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

寬度大於 1 像素的筆應始終具有PS_NULL、PS_SOLID或PS_INSIDEFRAME樣式。

如果筆具有PS_INSIDEFRAME樣式和與邏輯顏色表中的顏色不匹配的顏色,則筆將繪製為抖紅色。 如果筆寬度小於或等於 1,則PS_INSIDEFRAME樣式與PS_SOLID相同。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

## <a name="cpenfromhandle"></a><a name="fromhandle"></a>CPen:從手柄

返回指向給定 Windows `CPen` GDI 筆物件的句柄的物件的指標。

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>參數

*hPen*<br/>
`HPEN`句柄到 Windows GDI 筆。

### <a name="return-value"></a>傳回值

指向`CPen`物件的指標(如果成功);如果成功,則指向物件。否則 NULL。

### <a name="remarks"></a>備註

如果 `CPen` 物件沒有附加至控制代碼，會建立並附加暫存 `CPen` 物件。 此臨時`CPen`物件僅在下次應用程式在其事件迴圈中有空閑時間之前有效,此時將刪除所有臨時圖形物件。 換句話說,臨時物件僅在處理一個視窗消息期間有效。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

## <a name="cpengetextlogpen"></a><a name="getextlogpen"></a>CPen:獲取ExtLogPen

獲取`EXTLOGPEN`基礎結構。

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>參數

*pLogPen*<br/>
指向包含筆資訊的[EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)結構。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

結構`EXTLOGPEN`定義筆的樣式、寬度和畫筆屬性。 例如,調用`GetExtLogPen`以匹配筆的特定樣式。

有關筆屬性的資訊,請參閱 Windows SDK 中的以下主題:

- [取得物件](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)

- [洛彭](/windows/win32/api/wingdi/ns-wingdi-logpen)

- [ExtCreatePen](/windows/win32/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>範例

以下代碼示例演示了調用`GetExtLogPen`檢索筆的屬性,然後創建具有相同顏色的新修飾筆。

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

## <a name="cpengetlogpen"></a><a name="getlogpen"></a>CPen:獲取LogPen

獲取`LOGPEN`基礎結構。

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>參數

*pLogPen*<br/>
指向[LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)結構以包含有關筆的資訊。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

結構`LOGPEN`定義筆的樣式、顏色和圖案。

例如,調用`GetLogPen`以匹配筆的特定樣式。

有關筆屬性的資訊,請參閱 Windows SDK 中的以下主題:

- [取得物件](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [洛彭](/windows/win32/api/wingdi/ns-wingdi-logpen)

### <a name="example"></a>範例

以下代碼示例演示了調用`GetLogPen`以檢索筆字元,然後創建具有相同顏色的新實心筆。

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

## <a name="cpenoperator-hpen"></a><a name="operator_hpen"></a>CPen::操作員 HPEN

獲取`CPen`物件的附加 Windows GDI 句柄。

```
operator HPEN() const;
```

### <a name="return-value"></a>傳回值

如果成功,則對物件表示的 Windows`CPen`GDI 物件的句柄;如果成功,則對物件表示的 Windows GDI 物件的句柄。否則 NULL。

### <a name="remarks"></a>備註

此運算元是強制轉換運算符,支援直接使用 HPEN 物件。

有關使用圖形物件的詳細資訊,請參閱 Windows SDK 中的[圖形物件](/windows/win32/gdi/graphic-objects)一文。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>另請參閱

[CGdiObject 類別](../../mfc/reference/cgdiobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CBrush 類別](../../mfc/reference/cbrush-class.md)
