---
title: CWinFormsDialog 類別
ms.date: 03/27/2019
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
ms.openlocfilehash: 3772033df59e065cedca61012cd479c812cf5b66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367432"
---
# <a name="cwinformsdialog-class"></a>CWinFormsDialog 類別

裝載 Windows Form 使用者控制項的 MFC 對話方塊類別包裝函式。

## <a name="syntax"></a>語法

```
template <typename TManagedControl>
class CWinFormsDialog :
    public CDialog
```

#### <a name="parameters"></a>參數

*T託管控制*<br/>
要在 MFC 應用程式中顯示的 .NET 框架使用者控制項。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWinForms對話::CwinForms對話](#cwinformsdialog)|建構 `CWinFormsDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinForms對話:取得控制](#getcontrol)|檢索對 Windows 表單使用者控制件的引用。|
|[CWinForms對話::取得控制句柄](#getcontrolhandle)|檢索 Windows 窗體使用者控件的視窗句柄。|
|[CwinForms對話::OnInitDialog](#oninitdialog)|通過在 MFC 對話方塊上創建和託管 Windows 窗體使用者控制件來初始化 MFC 對話框。|

### <a name="public-operators"></a>公用運算子

|名稱||
|----------|-|
|[CWinForms對話::運算符 -&gt;](#operator_-_gt)|替換[CWinFormsDialog::獲取](#getcontrol)運算式中的控制。|
|[CWinForms對話::操作員 T 託管控制*](#operator-tmanagedcontrol-hat)|將類型強制轉換為對 Windows 表單使用者控制的參考。|

## <a name="remarks"></a>備註

`CWinFormsDialog`是承載 Windows 窗體使用者控制件的 MFC 對話方塊類[( CDialog](../../mfc/reference/cdialog-class.md)) 的包裝器。 這允許在模態或無模式 MFC 對話框上顯示 .NET 框架控制項。

有關使用 Windows 窗體的詳細資訊,請參閱[在 MFC 中使用 Windows 窗體使用者控制件](../../dotnet/using-a-windows-form-user-control-in-mfc.md),並將[Windows 元件使用者控制元件託管為 MFC 對話框](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)。

## <a name="requirements"></a>需求

**標題:** afxwinforms.h

## <a name="cwinformsdialogcwinformsdialog"></a><a name="cwinformsdialog"></a>CWinForms對話::CwinForms對話

建構 `CWinFormsDialog` 物件。

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>參數

*nIDTemplate*<br/>
包含對話方塊樣本資源的 ID。 使用對話框編輯器創建對話方塊樣本並將其存儲在應用程式的資源腳本檔中。 有關對話框樣本的詳細資訊,請參閱[CDialog 類別](../../mfc/reference/cdialog-class.md)。

## <a name="cwinformsdialoggetcontrol"></a><a name="getcontrol"></a>CWinForms對話:取得控制

檢索對 Windows 表單使用者控制件的引用。

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>傳回值

在 MFC 對話方塊中傳回對 Windows 窗體控制的參考。

## <a name="cwinformsdialoggetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinForms對話::取得控制句柄

檢索 Windows 窗體使用者控件的視窗句柄。

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>傳回值

將視窗句柄返回到 Windows 表單使用者控制件。

## <a name="cwinformsdialogoninitdialog"></a><a name="oninitdialog"></a>CwinForms對話::OnInitDialog

通過在 MFC 對話方塊上創建和託管 Windows 窗體使用者控制件來初始化 MFC 對話框。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

Boolean 值,用於指定應用程式是否已將輸入焦點設置為對話方塊中的一個控制項。 如果`OnInitDialog`返回非零,Windows 會將輸入焦點設置到對話方塊中的第一個控制項。 僅當應用程式已顯式將輸入焦點設置為對話方塊中的一個控制項時,此方法才能返回 0。

### <a name="remarks"></a>備註

建立 MFC 對話方塊(使用從[CDialog](../../mfc/reference/cdialog-class.md)繼承的[建立](../../mfc/reference/cdialog-class.md#create)、[建立間接](../../mfc/reference/cdialog-class.md#createindirect)或[DoModal](../../mfc/reference/cdialog-class.md#domodal)方法)時,將發送WM_INITDIALOG訊息並調用此方法。 它在對話框上創建 Windows 表單控制項的實體,並調整對話框的大小以適應使用者控制件的大小。 然後,它將在 MFC 對話框中承載新控制項。

如果在初始化對話方塊時需要執行特殊處理,則重寫此成員函數。 有關使用此方法的詳細資訊,請參閱[CDialog:onInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)。

## <a name="cwinformsdialogoperator--gt"></a><a name="operator_-_gt"></a>CWinForms對話::運算符 -&gt;

替換[CWinFormsDialog::獲取](#getcontrol)運算式中的控制。

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>備註

此運算元提供了一個方便的語法,`GetControl`在運算式中替換。

有關使用 Windows 表單的資訊,請參閱[在 MFC 中使用 Windows 元件使用者控制件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="cwinformsdialogoperator-tmanagedcontrol"></a><a name="operator-tmanagedcontrol-hat"></a>CWinForms對話::操作員 T 託管控制*

將類型強制轉換為對 Windows 表單使用者控制的參考。

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>備註

此運算符強制轉換類型作為對 Windows 窗體控制件的引用。 它用於將`CWinFormsDialog<TManagedControl>`對話框傳遞給接受指向 Windows 窗體使用者控件物件的指標的函數。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
