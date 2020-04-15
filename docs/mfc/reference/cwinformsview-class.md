---
title: CWinFormsView 類別
ms.date: 11/04/2016
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
ms.openlocfilehash: 6eb6b9e385e9dbc96eb3b62ffb80909e54569e97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369597"
---
# <a name="cwinformsview-class"></a>CWinFormsView 類別

提供可將 Windows Form 控制項裝載為 MFC 檢視的一般功能。

## <a name="syntax"></a>語法

```
class CWinFormsView : public CView;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWinForms查看:CwinForms查看](#cwinformsview)|建構 `CWinFormsView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinForms檢視:取得控制](#getcontrol)|檢索指向 Windows 表單控制件的指標。|

### <a name="public-operators"></a>公用運算子

|名稱||
|----------|-|
|[CWinForms查看::操作員控制*](#operator_control)|將類型轉換為指向 Windows 表單控制件的指標。|

## <a name="remarks"></a>備註

MFC`CWinFormsView`使用 類在 MFC 檢視中託管 .NET 框架 Windows 窗體控制項。 控件是本機視圖的子級,並佔據 MFC 視圖的整個工作區。 結果類似於`CFormView`檢視,允許您利用 Windows 窗體設計器和運行時創建豐富的基於窗體的檢視。

有關使用 Windows 表單的詳細資訊,請參閱[在 MFC 中使用 Windows 元件使用者控制件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

> [!NOTE]
> MFC Windows 窗體整合僅適用於與 MFC 動態連結的專案(其中定義了 AFXDLL 的專案)。

> [!NOTE]
> CWinFormsView 不支援 MFC 拆分器視窗[(CSplitterWnd 類](../../mfc/reference/csplitterwnd-class.md))。 目前僅支援 Windows 窗體拆分器控制件。

## <a name="requirements"></a>需求

**標題:** afxwinforms.h

## <a name="cwinformsviewcwinformsview"></a><a name="cwinformsview"></a>CWinForms查看:CwinForms查看

建構 `CWinFormsView` 物件。

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>參數

*p 託管檢視類型*<br/>
指向 Windows 窗體使用者控件的數據類型的指標。

### <a name="example"></a>範例

在下面的`CUserView`範例中,類`CWinFormsView`繼承並將的`UserControl1`類型傳遞`CWinFormsView`給構造函數。 `UserControl1`是 ControlLibrary1.dll 中的自定義控制項。

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

## <a name="cwinformsviewgetcontrol"></a><a name="getcontrol"></a>CWinForms檢視:取得控制

檢索指向 Windows 表單控制件的指標。

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>傳回值

`System.Windows.Forms.Control` 物件的指標。

### <a name="remarks"></a>備註

有關如何使用 Windows 表單的範例,請參閱在[MFC 中使用 Windows 元件使用者控制件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="cwinformsviewoperator-control"></a><a name="operator_control"></a>CWinForms查看::操作員控制*

將類型轉換為指向 Windows 表單控制件的指標。

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>備註

此運算子允許您將`CWinFormsView`檢視傳遞給接受指向類型<xref:System.Windows.Forms.Control>Windows 窗體控件的指標的函數。

### <a name="example"></a>範例

  請參考[CWinFormsView:取得控制](#getcontrol)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl 類別](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog 類別](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView 類別](../../mfc/reference/cformview-class.md)
