---
title: CGdiObject 類別
ms.date: 11/04/2016
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
ms.openlocfilehash: 0cd7a0e0ed500ee9394b00e8906640e9f950163b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373730"
---
# <a name="cgdiobject-class"></a>CGdiObject 類別

為各種 Windows 繪圖裝置介面 (GDI) 物件 (例如點陣圖、區域、筆刷、畫筆、調色盤和字型) 提供基底類別。

## <a name="syntax"></a>語法

```
class CGdiObject : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CGdiObject:CGdiObject](#cgdiobject)|建構 `CGdiObject` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CGdiObject::附加](#attach)|將 Windows GDI 物件`CGdiObject`附加到物件。|
|[CGdiObject::建立股票物件](#createstockobject)|檢索對其中一個 Windows 預定義的庫存筆、畫筆或字體的句柄。|
|[CGdiObject::DeleteObject](#deleteobject)|通過釋放與該物件關聯的所有系統存儲,`CGdiObject`從記憶體中刪除附加到該物件的 Windows GDI 物件。|
|[CGdiObject::DeleteTempMap](#deletetempmap)|刪除`FromHandle``CGdiObject`由建立的任何臨時物件。|
|[CGdiObject::D埃塔奇](#detach)|從`CGdiObject`物件分離 Windows GDI 物件,並將句柄返回到 Windows GDI 物件。|
|[CGdiObject::從手柄](#fromhandle)|返回指向給定 Windows `CGdiObject` GDI 物件的句柄的物件的指標。|
|[CGdiObject:取得物件](#getobject)|使用描述附加到`CGdiObject`物件的 Windows GDI 物件的數據填充緩衝區。|
|[CGdiObject:取得物件類型](#getobjecttype)|檢索 GDI 物件的類型。|
|[CGdiObject:取得安全處理](#getsafehandle)|傳`m_hObject`**回 ,除非這是**NULL,在這種情況下傳回 NULL。|
|[CGdiObject:未實作物件](#unrealizeobject)|重置畫筆的原點或重置邏輯調色板。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CGdiObject::操作員!*](#operator_neq)|確定兩個 GDI 物件在邏輯上是否不相等。|
|[CGdiObject::運算符 |](#operator_eq_eq)|確定兩個 GDI 物件在邏輯上是否相等。|
|[CGdiObject::操作員HGDIOBJ](#operator_hgdiobj)|檢索附加的 Windows GDI 物件的 HANDLE。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CGdiObject:m_hObject](#m_hobject)|包含附加到此物件的 HBITMAP、HPALETTE、HRGN、HBRUSH、HPEN 或 HFONT 的手柄。|

## <a name="remarks"></a>備註

您從不直接建立`CGdiObject`。 相反,您從其派生類之一(如`CPen`或`CBrush`)創建物件。

有關 的詳細`CGdiObject`資訊 ,請參閱[圖形物件](../../mfc/graphic-objects.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cgdiobjectattach"></a><a name="attach"></a>CGdiObject::附加

將 Windows GDI 物件`CGdiObject`附加到物件。

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>參數

*hObject*<br/>
Windows GDI 物件的句柄(例如,HPEN 或 HBRUSH)。

### <a name="return-value"></a>傳回值

如果附件成功,則非零;否則 0。

## <a name="cgdiobjectcgdiobject"></a><a name="cgdiobject"></a>CGdiObject:CGdiObject

建構 `CGdiObject` 物件。

```
CGdiObject();
```

### <a name="remarks"></a>備註

您從不直接建立`CGdiObject`。 相反,您從其派生類之一(如`CPen`或`Cbrush`)創建物件。

## <a name="cgdiobjectcreatestockobject"></a><a name="createstockobject"></a>CGdiObject::建立股票物件

檢索對預定義的庫存 Windows GDI 筆、畫筆或字體之一的句柄,並將 GDI 物件附加到`CGdiObject`物件。

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定所需庫存物件的類型的常量。 有關適當值的說明,請參閱 Windows SDK 中[GetStockObject](/windows/win32/api/wingdi/nf-wingdi-getstockobject)的參數*fnObject。*

### <a name="return-value"></a>傳回值

如果函式成功則為非零，否則為 0。

### <a name="remarks"></a>備註

使用與 Windows GDI 物件類型對應的派生類之一調用此函`CPen`數,例如 對於股票筆。

## <a name="cgdiobjectdeleteobject"></a><a name="deleteobject"></a>CGdiObject::DeleteObject

通過釋放與 Windows GDI 物件關聯的所有系統存儲,從記憶體中刪除附加的 Windows GDI 物件。

```
BOOL DeleteObject();
```

### <a name="return-value"></a>傳回值

如果成功刪除 GDI 物件,則非零;否則 0。

### <a name="remarks"></a>備註

與`CGdiObject`物件關聯的存儲不受此調用的影響。 應用程式不應調用`DeleteObject`當前選擇到`CGdiObject`設備 上下文中的物件。

刪除模式畫筆時,不會刪除與畫筆關聯的位圖。 必須獨立刪除點陣圖。

## <a name="cgdiobjectdeletetempmap"></a><a name="deletetempmap"></a>CGdiObject::DeleteTempMap

由`CWinApp`空閒時間處理程式自動呼叫,`DeleteTempMap`刪除`CGdiObject``FromHandle`是由建立的任何臨時物件。

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>備註

`DeleteTempMap`在刪除`CGdiObject``CGdiObject`物件之前,分離附加到臨時物件的 Windows GDI 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

## <a name="cgdiobjectdetach"></a><a name="detach"></a>CGdiObject::D埃塔奇

從`CGdiObject`物件分離 Windows GDI 物件,並將句柄返回到 Windows GDI 物件。

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>傳回值

A`HANDLE`到 Windows GDI 物件分離;否則 NULL,如果沒有附加 GDI 物件。

## <a name="cgdiobjectfromhandle"></a><a name="fromhandle"></a>CGdiObject::從手柄

返回指向給定 Windows `CGdiObject` GDI 物件的句柄的物件的指標。

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>參數

*hObject*<br/>
Windows GDI 物件的句柄。

### <a name="return-value"></a>傳回值

指向`CGdiObject`的指標可能是臨時的或永久性的。

### <a name="remarks"></a>備註

如果`CGdiObject`物件尚未附加到 Windows GDI 物件,`CGdiObject`則創建並附加 臨時物件。

此臨時`CGdiObject`物件僅在下次應用程式在其事件迴圈中有空閑時間之前有效,此時將刪除所有臨時圖形物件。 另一種說法是臨時物件僅在處理一個視窗消息期間有效。

## <a name="cgdiobjectgetobject"></a><a name="getobject"></a>CGdiObject:取得物件

用定義指定物件的數據填充緩衝區。

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>參數

*n( N) Count*<br/>
指定要複製到*lpObject*緩衝區的位元組數。

*lpObject*<br/>
指向使用者提供的緩衝區,該緩衝區用於接收資訊。

### <a name="return-value"></a>傳回值

檢索的位元組數;否則 0 如果發生錯誤。

### <a name="remarks"></a>備註

函式檢索其類型取決於圖形物件類型的資料結構,如下清單所示:

|Object|緩衝區型別|
|------------|-----------------|
|`CPen`|[洛彭](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[記錄筆刷](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[紀錄](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[點陣圖](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|不支援|

如果物件是`CBitmap`物件`GetObject`, 則僅返回位元圖的寬度、高度和顏色格式資訊。 可以使用[CBitmap::getBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits)檢索實際位。

如果物件是`CPalette`物件`GetObject`, 則檢索指定調色板中條目數的 WORD。 函數不檢索定義調色板的[LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette)結構。 應用程式可以通過調用[CPalette::getPalette 條目](../../mfc/reference/cpalette-class.md#getpaletteentries)來獲取有關調色板條目的資訊。

## <a name="cgdiobjectgetobjecttype"></a><a name="getobjecttype"></a>CGdiObject:取得物件類型

檢索 GDI 物件的類型。

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>傳回值

對象的類型(如果成功);否則 0。 這個值可以是下列值之一：

- OBJ_BITMAP位圖

- OBJ_BRUSH筆刷

- OBJ_FONT字型

- OBJ_PAL調色板

- OBJ_PEN筆

- OBJ_EXTPEN延伸筆

- OBJ_REGION地區

- OBJ_DC裝置上下文

- OBJ_MEMDC記憶體裝置上下文

- OBJ_METAFILE中繼檔

- OBJ_METADC中繼檔裝置

- OBJ_ENHMETAFILE增強的中繼檔

- OBJ_ENHMETADC增強中繼裝置

## <a name="cgdiobjectgetsafehandle"></a><a name="getsafehandle"></a>CGdiObject:取得安全處理

傳`m_hObject`**回 ,除非這是**NULL,在這種情況下傳回 NULL。

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>傳回值

附加 Windows GDI 物件的句柄;否則 NULL,如果沒有附加任何物件。

### <a name="remarks"></a>備註

這是常規句柄介面範例的一部分,當 NULL 是句柄的有效值或特殊值時,這非常有用。

### <a name="example"></a>範例

  請參考[CWnd 的範例::正在啟用視窗](../../mfc/reference/cwnd-class.md#iswindowenabled)。

## <a name="cgdiobjectm_hobject"></a><a name="m_hobject"></a>CGdiObject:m_hObject

包含附加到此物件的 HBITMAP、HRGN、HBRUSH、HPEN、HPALETTE 或 HFONT 的手柄。

```
HGDIOBJ m_hObject;
```

## <a name="cgdiobjectoperator-"></a><a name="operator_neq"></a>CGdiObject::操作員!*

確定兩個 GDI 物件在邏輯上是否不相等。

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>參數

*obj*<br/>
指向現有`CGdiObject`的指標。

### <a name="remarks"></a>備註

確定左側的 GDI 物件是否不等於右側的 GDI 物件。

## <a name="cgdiobjectoperator-"></a><a name="operator_eq_eq"></a>CGdiObject::運算符 |

確定兩個 GDI 物件在邏輯上是否相等。

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>參數

*obj*<br/>
已對現有的`CGdiObject`參考 。

### <a name="remarks"></a>備註

確定左側的 GDI 物件是否等於右側的 GDI 物件。

## <a name="cgdiobjectoperator-hgdiobj"></a><a name="operator_hgdiobj"></a>CGdiObject::操作員HGDIOBJ

檢索附加 Windows GDI 物件的 HANDLE;否則 NULL,如果沒有附加任何物件。

```
operator HGDIOBJ() const;
```

## <a name="cgdiobjectunrealizeobject"></a><a name="unrealizeobject"></a>CGdiObject:未實作物件

重置畫筆的原點或重置邏輯調色板。

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

雖然`UnrealizeObject``CGdiObject`是類的成員函數,但應僅調用`CBrush``CPalette`或 物件。

對於`CBrush`物件,`UnrealizeObject`指示系統在下次選擇給定畫筆到設備上下文中時重置其原點。 如果對像是`CPalette`物件,則`UnrealizeObject`指示系統實現調色板,就好像它以前尚未實現一樣。 下次應用程式調用指定調色板的[CDC::實現調色板](../../mfc/reference/cdc-class.md#realizepalette)功能時,系統將邏輯調色板完全重新映射到系統調色板。

該`UnrealizeObject`函數不應與庫存物件一起使用。 每當`UnrealizeObject`設定新的畫筆源時(透過[CDC::SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg)函數),都必須調用該函數。 不得`UnrealizeObject`為當前選定的畫筆或任何顯示上下文的當前選定調色板調用該函數。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CBitmap 類別](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush 類別](../../mfc/reference/cbrush-class.md)<br/>
[CFont 類別](../../mfc/reference/cfont-class.md)<br/>
[CPalette 類別](../../mfc/reference/cpalette-class.md)<br/>
[CPen 類別](../../mfc/reference/cpen-class.md)<br/>
[CRgn 類別](../../mfc/reference/crgn-class.md)
