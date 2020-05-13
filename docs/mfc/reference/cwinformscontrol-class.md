---
title: CWinFormsControl 類別
ms.date: 11/04/2016
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
ms.openlocfilehash: c91f50be1ea30efac81ff67c43633bedd7b0ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377184"
---
# <a name="cwinformscontrol-class"></a>CWinFormsControl 類別

提供裝載 Windows Form 控制項的基本功能。

## <a name="syntax"></a>語法

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>參數

*T託管控制*<br/>
要在 MFC 應用程式中顯示的 .NET 框架 Windows 窗體控制件。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWinForms控制:CwinForms控制](#cwinformscontrol)|構造 MFC Windows 表單控制件包裝物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinForms控制:建立託管控制](#createmanagedcontrol)|在 MFC 容器中創建 Windows 表單控制元件。|
|[CWinForms控制:取得控制](#getcontrol)|檢索指向 Windows 表單控制件的指標。|
|[CWinForms控制:取得控制句柄](#getcontrolhandle)|檢索 Windows 窗體控件的句柄。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CWinForms控制::運算符 -&gt;](#operator_-_gt)|替換[CWinForms 控制:獲取](#getcontrol)運算式中的控制。|
|[CWinForms控制::操作員 T 託管控制*](#operator_tmanagedcontrol)|將類型轉換為指向 Windows 表單控制件的指標。|

## <a name="remarks"></a>備註

該`CWinFormsControl`類提供用於託管 Windows 表單控制項的基本功能。

有關使用 Windows 表單的詳細資訊,請參閱[在 MFC 中使用 Windows 元件使用者控制件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

MFC 代碼不應緩存視窗句柄(通常存儲在`m_hWnd`中)。 某些 Windows 表單元件屬性要求`Window``DestroyWindow`使用和銷毀和重新建立`CreateWindow`基礎 Win32。 MFC Windows 窗體`Destroy`實現`Create`處理`m_hWnd`要更新 成員的控制項的和事件。

> [!NOTE]
> MFC Windows 窗體整合僅適用於與 MFC 動態連結的專案(其中定義了 AFXDLL)。

## <a name="requirements"></a>需求

**標題:** afxwinforms.h

## <a name="cwinformscontrolcreatemanagedcontrol"></a><a name="createmanagedcontrol"></a>CWinForms控制:建立託管控制

在 MFC 容器中創建 Windows 表單控制元件。

```
inline BOOL CreateManagedControl(
    System::Type^ pType,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID)
inline BOOL CreateManagedControl(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);

inline BOOL CreateManagedControl(
    DWORD dwStyle,
    int nPlaceHolderID,
    CWnd* pParentWnd);

inline BOOL CreateManagedControl(
    typename TManagedControl^ pControl,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);
```

### <a name="parameters"></a>參數

*p 型態*<br/>
要創建的控制項的數據類型。 必須為[類型](/dotnet/api/system.type)資料類型。

*dwStyle*<br/>
要應用於控制件的視窗樣式。 指定[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的組合。 目前,僅支援以下樣式:WS_TABSTOP、WS_VISIBLE、WS_DISABLED和WS_GROUP。

*矩形*<br/>
定義控制器左上角與右下角座標(僅首次過載)的[RECT 結構](/windows/win32/api/windef/ns-windef-rect)。

*nPlaceHolderID*<br/>
放置在資源編輯器中的靜態占位符控件的句柄。 新創建的 Windows 窗體控制項將取代靜態控制項,假設其位置、z 順序和樣式(僅第二次重載)。

*pparentwnd*<br/>
指向父視窗的指標。

*nID*<br/>
要分配給新創建的控制項的資源ID號。

*pControl*<br/>
要與[CWinFormsControl 控制](../../mfc/reference/cwinformscontrol-class.md)物件關聯的 Windows 窗體控件的實例(僅限第四次重載)。

### <a name="return-value"></a>傳回值

如果成功,則返回一個非零值。 如果不成功,則返回零。

### <a name="remarks"></a>備註

此方法實例化 MFC 容器中的 .NET 框架 Windows 窗體控件。

方法的第一個重載接受 .NET 框架數據類型*pType,* 以便 MFC 可以實例化此類型的新物件。 *pType*必須是[類型](/dotnet/api/system.type)資料類型。

方法的第二個重載基於`TManagedControl``CWinFormsControl`類的範本參數創建 Windows 窗體控件。 控制項大小和位置以傳遞給方法`RECT`的結構。 只有*dwStyle*才對樣式很重要。

方法的第三個重載將創建一個 Windows 窗體控件,該控件將替換靜態控制項,將其破壞並假定其位置、z 順序和樣式。 靜態控制項僅用作 Windows 表單控制件的占位符。 創建控制項時,此重載將*dwStyle*中的樣式與靜態控制件的資源樣式合併。

方法的第四個重載允許您傳遞 MFC 將包裝的已實例化 Windows 窗體控件*pControl。* 它必須與`TManagedControl``CWinFormsControl`類的範本參數類型相同。

有關使用 Windows 表單元件的範例[,請參閱在 MFC 中使用 Windows 元件使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="cwinformscontrolcwinformscontrol"></a><a name="cwinformscontrol"></a>CWinForms控制:CwinForms控制

構造 MFC Windows 表單控制件包裝物件。

```
CWinFormsControl();
```

### <a name="remarks"></a>備註

當您調用[CWinFormsControl::建立託管控制](#createmanagedcontrol)時,Windows 窗體控制項將實例化。

## <a name="cwinformscontrolgetcontrol"></a><a name="getcontrol"></a>CWinForms控制:取得控制

檢索指向 Windows 表單控制件的指標。

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>傳回值

返回指向 Windows 窗體控件的指標。

### <a name="example"></a>範例

  請參考[CWinForms 控制:建立託管控制](#createmanagedcontrol)。

## <a name="cwinformscontrolgetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinForms控制:取得控制句柄

檢索 Windows 窗體控件的句柄。

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>傳回值

將句柄返回到 Windows 表單控制元件。

### <a name="remarks"></a>備註

`GetControlHandle`是返回存儲在 .NET Framework 控制項屬性中的視窗句柄的幫助器方法。 在調用[CWnd::附加](../../mfc/reference/cwnd-class.md#attach)期間,視窗句柄值將複製到[CWnd::m_hWnd。](../../mfc/reference/cwnd-class.md#m_hwnd)

## <a name="cwinformscontroloperator--gt"></a><a name="operator_-_gt"></a>CWinForms控制::運算符 -&gt;

替換[CWinForms 控制:獲取](#getcontrol)運算式中的控制。

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>備註

此運算元提供了一個方便的語法,`GetControl`在運算式中替換。

有關 Windows 表單的詳細資訊,請參閱[在 MFC 中使用 Windows 元件使用者控制件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="cwinformscontroloperator-tmanagedcontrol"></a><a name="operator_tmanagedcontrol"></a>CWinForms控制::操作員 T 託管控制*

將類型轉換為指向 Windows 表單控制件的指標。

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>備註

此運算符傳遞給`CWinFormsControl<TManagedControl>`接受指向 Windows 窗體控件的指標的函數。

## <a name="see-also"></a>另請參閱

[CWinFormsDialog 類別](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)
