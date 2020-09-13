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
ms.openlocfilehash: a25823982b9276309e99a2a26cef8d6fe2e764bd
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040661"
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

*TManagedControl*<br/>
要在 MFC 應用程式中顯示的 .NET Framework 使用者控制項。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|建構 `CWinFormsDialog` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinFormsDialog::GetControl](#getcontrol)|抓取 Windows Forms 使用者控制項的參考。|
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|抓取 Windows Forms 使用者控制項的視窗控制碼。|
|[CWinFormsDialog：： OnInitDialog](#oninitdialog)|藉由在其上建立並裝載 Windows Forms 的使用者控制項，初始化 MFC 對話方塊。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-|
|[CWinFormsDialog：： operator-&gt;](#operator_-_gt)|取代運算式中的 [CWinFormsDialog：： GetControl](#getcontrol) 。|
|[CWinFormsDialog：： operator TManagedControl ^](#operator-tmanagedcontrol-hat)|將型別轉換為 Windows Forms 使用者控制項的參考。|

## <a name="remarks"></a>備註

`CWinFormsDialog` 是 MFC 對話方塊類別的包裝函式， ( 裝載 Windows Forms 使用者控制項的 [CDialog](../../mfc/reference/cdialog-class.md)) 。 這可讓您在強制回應或非模式 MFC 對話方塊上顯示 .NET Framework 控制項。

如需使用 Windows Forms 的詳細資訊，請參閱 [在 mfc 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md) ，以及將 [Windows Form 使用者控制項裝載為 mfc 對話方塊](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)。

## <a name="requirements"></a>需求

**標頭：** afxwinforms。h

## <a name="cwinformsdialogcwinformsdialog"></a><a name="cwinformsdialog"></a> CWinFormsDialog::CWinFormsDialog

建構 `CWinFormsDialog` 物件。

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>參數

*nIDTemplate*<br/>
包含對話方塊範本資源的識別碼。 使用對話方塊編輯器建立對話方塊範本，並將它儲存在應用程式的資源腳本檔案中。 如需對話方塊範本的詳細資訊，請參閱 [CDialog 類別](../../mfc/reference/cdialog-class.md)。

## <a name="cwinformsdialoggetcontrol"></a><a name="getcontrol"></a> CWinFormsDialog::GetControl

抓取 Windows Forms 使用者控制項的參考。

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>傳回值

傳回 MFC 對話方塊中 Windows Forms 控制項的參考。

## <a name="cwinformsdialoggetcontrolhandle"></a><a name="getcontrolhandle"></a> CWinFormsDialog::GetControlHandle

抓取 Windows Forms 使用者控制項的視窗控制碼。

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>傳回值

傳回 Windows Forms 使用者控制項的視窗控制碼。

## <a name="cwinformsdialogoninitdialog"></a><a name="oninitdialog"></a> CWinFormsDialog：： OnInitDialog

藉由在其上建立並裝載 Windows Forms 的使用者控制項，初始化 MFC 對話方塊。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>傳回值

布林值，指定應用程式是否已將輸入焦點設定為對話方塊中的其中一個控制項。 如果傳回 `OnInitDialog` 非零值，Windows 會將輸入焦點設定至對話方塊中的第一個控制項。 只有當應用程式已將輸入焦點明確設定至對話方塊中的其中一個控制項時，此方法才會傳回0。

### <a name="remarks"></a>備註

使用繼承自[CDialog](../../mfc/reference/cdialog-class.md)) 的[Create](../../mfc/reference/cdialog-class.md#create)、 [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect)或[DoModal](../../mfc/reference/cdialog-class.md#domodal)方法 (建立 MFC 對話方塊時，會傳送 WM_INITDIALOG 訊息，並呼叫這個方法。 它會在對話方塊上建立 Windows Forms 控制項的實例，並調整對話方塊的大小以容納使用者控制項的大小。 然後，它會在 MFC 對話方塊中裝載新的控制項。

如果您需要在初始化對話方塊時執行特殊處理，請覆寫這個成員函式。 如需使用此方法的詳細資訊，請參閱 [CDialog：： OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)。

## <a name="cwinformsdialogoperator--gt"></a><a name="operator_-_gt"></a> CWinFormsDialog：： operator-&gt;

取代運算式中的 [CWinFormsDialog：： GetControl](#getcontrol) 。

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>備註

這個運算子提供可在運算式中取代的便利語法 `GetControl` 。

如需使用 Windows Forms 的詳細資訊，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="cwinformsdialogoperator-tmanagedcontrol"></a><a name="operator-tmanagedcontrol-hat"></a> CWinFormsDialog：： operator TManagedControl ^

將型別轉換為 Windows Forms 使用者控制項的參考。

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>備註

這個運算子會將型別轉換為 Windows Forms 控制項的參考。 它是用來將 `CWinFormsDialog<TManagedControl>` 對話方塊傳遞至接受 Windows Forms 使用者控制項物件之指標的函式。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
