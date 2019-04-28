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
ms.openlocfilehash: f4a5e6b88527dad8606092ccebd4899bba5181f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323292"
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
|[CWinFormsView::CWinFormsView](#cwinformsview)|建構 `CWinFormsView` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWinFormsView::GetControl](#getcontrol)|擷取至 Windows Forms 控制項的指標。|

### <a name="public-operators"></a>公用運算子

|名稱||
|----------|-|
|[CWinFormsView::operator 控制項 ^](#operator_control)|將類型轉換至 Windows Form 控制項的指標。|

## <a name="remarks"></a>備註

MFC 使用`CWinFormsView`裝載.NET Framework Windows Form 控制項在 MFC 檢視類別。 控制項子系的原生的檢視，而且佔用的 MFC 檢視整個工作區。 結果會類似於`CFormView`檢視，可讓您利用 Windows Form 設計工具和執行階段用來建立豐富的以 form 為基礎的檢視。

如需有關如何使用 Windows Form 的詳細資訊，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

> [!NOTE]
>  MFC Windows Form 整合只適用於以動態方式連結 MFC 專案 （AFXDLL 定義所在的專案）。

> [!NOTE]
>  CWinFormsView 不支援 MFC 的分隔器視窗 ( [CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md))。 目前只有 Windows Form 分隔器支援控制。

## <a name="requirements"></a>需求

**標頭：** afxwinforms.h

##  <a name="cwinformsview"></a>  CWinFormsView::CWinFormsView

建構 `CWinFormsView` 物件。

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>參數

*pManagedViewType*<br/>
Windows Form 使用者控制項的資料類型的指標。

### <a name="example"></a>範例

在下列範例中，`CUserView`類別繼承自`CWinFormsView`，並將傳遞的型別`UserControl1`到`CWinFormsView`建構函式。 `UserControl1` 是 ControlLibrary1.dll 自訂控制項。

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

##  <a name="getcontrol"></a>  CWinFormsView::GetControl

擷取至 Windows Forms 控制項的指標。

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>傳回值

`System.Windows.Forms.Control` 物件的指標。

### <a name="remarks"></a>備註

如需如何使用 Windows Form 的範例，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

##  <a name="operator_control"></a>  CWinFormsView::operator 控制項 ^

將類型轉換至 Windows Form 控制項的指標。

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>備註

此運算子可讓您傳遞`CWinFormsView`檢視，以接受 Windows Form 控制項的類型指標的函式<xref:System.Windows.Forms.Control>。

### <a name="example"></a>範例

  請參閱[CWinFormsView::GetControl](#getcontrol)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl 類別](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog 類別](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView 類別](../../mfc/reference/cformview-class.md)
