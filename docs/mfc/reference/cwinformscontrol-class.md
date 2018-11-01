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
ms.openlocfilehash: c27bcfa88ec5ba8b330a62f6ecfbad7e10a54d6a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547481"
---
# <a name="cwinformscontrol-class"></a>CWinFormsControl 類別

提供裝載 Windows Form 控制項的基本功能。

## <a name="syntax"></a>語法

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>參數

*TManagedControl*<br/>
要顯示在 MFC 應用程式的.NET Framework Windows Form 控制項。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|建構 MFC Windows Form 控制項的包裝函式物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|在 MFC 容器中建立 Windows Form 控制項。|
|[CWinFormsControl::GetControl](#getcontrol)|擷取至 Windows Forms 控制項的指標。|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|擷取 Windows Form 控制項的控制代碼。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CWinFormsControl::operator-&gt;](#operator_-_gt)|會取代[CWinFormsControl::GetControl](#getcontrol)運算式中。|
|[CWinFormsControl::operator TManagedControl ^](#operator_tmanagedcontrol)|將類型轉換至 Windows Form 控制項的指標。|

## <a name="remarks"></a>備註

`CWinFormsControl`類別會提供裝載 Windows Form 控制項的基本功能。

如需有關如何使用 Windows Form 的詳細資訊，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

您的 MFC 程式碼應該不會快取視窗控制代碼 (通常儲存在`m_hWnd`)。 有些 Windows Form 控制項屬性需要基本的 Win32`Window`終結並重新建立使用`DestroyWindow`和`CreateWindow`。 MFC Windows Form 實作控制代碼`Destroy`並`Create`來更新控制項的事件`m_hWnd`成員。

> [!NOTE]
>  MFC Windows Form 整合只適用於動態連結 （AFXDLL 定義所在） 的 MFC 專案。

## <a name="requirements"></a>需求

**標頭：** afxwinforms.h

##  <a name="createmanagedcontrol"></a>  CWinFormsControl::CreateManagedControl

在 MFC 容器中建立 Windows Form 控制項。

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

*pType*<br/>
要建立之控制項的資料型別。 必須是[型別](https://msdn.microsoft.com/library/system.type)資料型別。

*cheaderctrl:: Create*<br/>
要套用至控制項的視窗樣式。 指定的組合[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 目前支援下列樣式： WS_TABSTOP、 WS_VISIBLE、 WS_DISABLED 和 WS_GROUP。

*rect*<br/>
A [RECT 結構](../../mfc/reference/rect-structure1.md)定義控制項的左上角和右下角的座標 （第一個多載只）。

*nPlaceHolderID*<br/>
靜態位置持有者控制項的控制代碼會放在資源編輯器中。 新建立的 Windows Form 控制項取代靜態控制項，並假設其位置、 疊置順序和樣式 （第二個多載只）。

*pParentWnd*<br/>
父視窗的指標。

*nID*<br/>
要指派給新建立之控制項的資源 ID 編號。

*pControl*<br/>
Windows Forms 控制項相關聯的執行個體[CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md)物件 （僅第四個多載）。

### <a name="return-value"></a>傳回值

如果成功，會傳回非零值。 如果不成功，會傳回零。

### <a name="remarks"></a>備註

這個方法具現化的 MFC 容器中.NET Framework Windows Form 控制項。

此方法的第一個多載接受.NET Framework 資料型別*pType*以便 MFC 可以具現化這個型別的新物件。 *pType*必須是[型別](https://msdn.microsoft.com/library/system.type)資料型別。

此方法的第二個多載會建立為基礎的 Windows Forms 控制項`TManagedControl`範本參數`CWinFormsControl`類別。 大小和位置的控制項根據`RECT`結構傳遞給方法。 只有*cheaderctrl:: Create*樣式很重要。

方法的第三個多載會建立 Windows Form 控制項，它會取代靜態控制項，終結它，並假設其位置、 疊置順序和樣式。 靜態控制項只會做 Windows Form 控制項的預留位置。 在建立控制項時，這個多載結合來自樣式*cheaderctrl:: Create*具有靜態控制項的資源的樣式。

方法的第四個多載可讓您傳入已具現化的 Windows Forms 控制項*pControl* ，MFC 會自動換行。 它必須是相同型別的`TManagedControl`範本參數`CWinFormsControl`類別。

請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)上使用 Windows Form 範例的控制。

##  <a name="cwinformscontrol"></a>  CWinFormsControl::CWinFormsControl

建構 MFC Windows Form 控制項的包裝函式物件。

```
CWinFormsControl();
```

### <a name="remarks"></a>備註

當您呼叫時，會具現化在 Windows Form 控制項[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)。

##  <a name="getcontrol"></a>  CWinFormsControl::GetControl

擷取至 Windows Forms 控制項的指標。

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>傳回值

加入 Windows Form 控制項中傳回的指標。

### <a name="example"></a>範例

  請參閱[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)。

##  <a name="getcontrolhandle"></a>  CWinFormsControl::GetControlHandle

擷取 Windows Form 控制項的控制代碼。

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>傳回值

傳回在 Windows Form 控制項的控制代碼。

### <a name="remarks"></a>備註

`GetControlHandle` 是 helper 方法會傳回儲存在.NET Framework 控制項屬性的視窗控制代碼。 視窗控制代碼值複製到[CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd)的呼叫期間[CWnd::Attach](../../mfc/reference/cwnd-class.md#attach)。

##  <a name="operator_-_gt"></a>  CWinFormsControl::operator-&gt;

會取代[CWinFormsControl::GetControl](#getcontrol)運算式中。

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>備註

此運算子會提供方便的語法，取代`GetControl`運算式中。

如需有關 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="operator_tmanagedcontrol"></a>  CWinFormsControl::operator TManagedControl ^

將類型轉換至 Windows Form 控制項的指標。

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>備註

此運算子會將傳送`CWinFormsControl<TManagedControl>`函式可接受的 Windows Form 控制項的指標。

## <a name="see-also"></a>另請參閱

[CWinFormsDialog 類別](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)
