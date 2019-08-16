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
ms.openlocfilehash: 75a6d7ea2b4f3ab229d7e3f4d411711261bb1b82
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502187"
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
要在 MFC 應用程式中顯示的 .NET Framework Windows Forms 控制項。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|構造 MFC Windows Forms 控制項包裝函式物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|在 MFC 容器中建立 Windows Forms 控制項。|
|[CWinFormsControl::GetControl](#getcontrol)|抓取 Windows Forms 控制項的指標。|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|抓取 Windows Forms 控制項的控制碼。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CWinFormsControl:: operator-&gt;](#operator_-_gt)|取代運算式中的[CWinFormsControl:: GetControl](#getcontrol) 。|
|[CWinFormsControl:: operator TManagedControl ^](#operator_tmanagedcontrol)|將類型轉換為 Windows Forms 控制項的指標。|

## <a name="remarks"></a>備註

`CWinFormsControl`類別提供裝載 Windows Forms 控制項的基本功能。

如需使用 Windows Forms 的詳細資訊, 請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

您的 MFC 程式碼不應該快取視窗控制碼`m_hWnd`(通常儲存在中)。 某些 Windows Forms 控制項屬性需要使用`Window` `DestroyWindow`和`CreateWindow`來終結並重新建立基礎 Win32。 MFC Windows Forms 的執行會處理`Destroy`控制項`Create`的和事件, 以更新`m_hWnd`成員。

> [!NOTE]
>  MFC Windows Forms 整合只適用于與 MFC 動態連結的專案 (其中定義了 AFXDLL)。

## <a name="requirements"></a>需求

**標頭:** afxwinforms。h

##  <a name="createmanagedcontrol"></a>CWinFormsControl::CreateManagedControl

在 MFC 容器中建立 Windows Forms 控制項。

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
要建立之控制項的資料類型。 必須是[類型](/dotnet/api/system.type)資料類型。

*dwStyle*<br/>
要套用至控制項的視窗樣式。 指定[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的組合。 目前僅支援下列樣式:WS_TABSTOP、WS_VISIBLE、WS_DISABLED 和 WS_GROUP。

*rect*<br/>
[矩形結構](/windows/win32/api/windef/ns-windef-rect), 定義控制項左上角和右下角的座標 (僅限第一個多載)。

*nPlaceHolderID*<br/>
放在資源編輯器中的靜態預留位置控制項的控制碼。 新建立的 Windows Forms 控制項會取代靜態控制項, 假設其位置、迭置順序和樣式 (僅限第二個多載)。

*pParentWnd*<br/>
父視窗的指標。

*nID*<br/>
要指派給新建立之控制項的資源識別碼 編號。

*pControl*<br/>
要與[CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md)物件相關聯之 Windows Forms 控制項的實例 (僅限第四個多載)。

### <a name="return-value"></a>傳回值

如果成功, 會傳回非零值。 如果失敗, 則傳回零。

### <a name="remarks"></a>備註

這個方法會將 MFC 容器中的 .NET Framework Windows Forms 控制項具現化。

方法的第一個多載會接受 .NET Framework 的資料類型*pType* , 讓 MFC 可以具現化這個類型的新物件。 *pType*必須是[類型](/dotnet/api/system.type)資料類型。

方法的第二個多載會根據`TManagedControl` `CWinFormsControl`類別的範本參數建立 Windows Forms 控制項。 控制項的大小和位置是以傳遞至方法的`RECT`結構為基礎。 只有*dwStyle*對樣式很重要。

方法的第三個多載會建立一個 Windows Forms 控制項, 以取代靜態控制項、將其終結, 並假設其位置、迭置順序和樣式。 靜態控制項僅作為 Windows Forms 控制項的預留位置。 建立控制項時, 這個多載會將*dwStyle*的樣式與靜態控制項的資源樣式結合。

方法的第四個多載可讓您傳入已具現化的 Windows Forms 控制項, 而 MFC 將會包裝。 它必須與`TManagedControl` `CWinFormsControl`類別的範本參數屬於相同的類型。

如需使用 Windows Form 控制項的範例, 請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="cwinformscontrol"></a>CWinFormsControl::CWinFormsControl

構造 MFC Windows Forms 控制項包裝函式物件。

```
CWinFormsControl();
```

### <a name="remarks"></a>備註

當您呼叫[CWinFormsControl:: CreateManagedControl](#createmanagedcontrol)時, 會具現化 Windows Forms 控制項。

##  <a name="getcontrol"></a>CWinFormsControl:: GetControl

抓取 Windows Forms 控制項的指標。

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>傳回值

傳回 Windows Forms 控制項的指標。

### <a name="example"></a>範例

  請參閱[CWinFormsControl:: CreateManagedControl](#createmanagedcontrol)。

##  <a name="getcontrolhandle"></a>CWinFormsControl::GetControlHandle

抓取 Windows Forms 控制項的控制碼。

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>傳回值

傳回 Windows Forms 控制項的控制碼。

### <a name="remarks"></a>備註

`GetControlHandle`是 helper 方法, 會傳回儲存在 .NET Framework 控制項屬性中的視窗控制碼。 視窗控制碼值會在呼叫[cwnd:: Attach](../../mfc/reference/cwnd-class.md#attach)期間複製到[Cwnd:: m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) 。

##  <a name="operator_-_gt"></a>CWinFormsControl:: operator-&gt;

取代運算式中的[CWinFormsControl:: GetControl](#getcontrol) 。

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>備註

這個運算子會提供可在運算式中`GetControl`取代的方便語法。

如需 Windows Forms 的詳細資訊, 請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="operator_tmanagedcontrol"></a>CWinFormsControl:: operator TManagedControl ^

將類型轉換為 Windows Forms 控制項的指標。

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>備註

這個運算子會`CWinFormsControl<TManagedControl>`傳遞至接受 Windows Forms 控制項之指標的函式。

## <a name="see-also"></a>另請參閱

[CWinFormsDialog 類別](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)
