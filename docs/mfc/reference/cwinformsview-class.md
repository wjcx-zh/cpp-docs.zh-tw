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
ms.openlocfilehash: 3c247babd2ec1057f1e24b8132ed81727a0fd402
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040648"
---
# <a name="cwinformsview-class"></a>CWinFormsView 類別

提供可將 Windows Form 控制項裝載為 MFC 檢視的一般功能。

## <a name="syntax"></a>語法

```
class CWinFormsView : public CView;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|Name|描述|
|----------|-----------------|
|[CWinFormsView::CWinFormsView](#cwinformsview)|建構 `CWinFormsView` 物件。|

### <a name="public-methods"></a>公用方法

|Name|描述|
|----------|-----------------|
|[CWinFormsView::GetControl](#getcontrol)|抓取 Windows Forms 控制項的指標。|

### <a name="public-operators"></a>公用運算子

|Name|描述|
|----------|-|
|[CWinFormsView：： operator Control ^](#operator_control)|將型別轉換為 Windows Forms 控制項的指標。|

## <a name="remarks"></a>備註

MFC 會使用 `CWinFormsView` 類別來裝載 MFC 視圖內的 .NET Framework Windows Forms 控制項。 控制項是原生視圖的子系，而且會佔用 MFC 視圖的整個工作區。 結果類似于 `CFormView` 視圖，可讓您利用 Windows Forms 設計工具和執行時間建立豐富的表單型視圖。

如需使用 Windows Forms 的詳細資訊，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

> [!NOTE]
> MFC Windows Forms 整合只適用于以動態方式連結至 MFC (專案的專案，其中定義了 AFXDLL) 。

> [!NOTE]
> CWinFormsView 不支援 MFC 分隔視窗 ( [CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md)) 。 目前只支援 Windows Forms 分隔器控制項。

## <a name="requirements"></a>需求

**標頭：** afxwinforms。h

## <a name="cwinformsviewcwinformsview"></a><a name="cwinformsview"></a> CWinFormsView::CWinFormsView

建構 `CWinFormsView` 物件。

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>參數

*pManagedViewType*<br/>
Windows Forms 使用者控制項之資料類型的指標。

### <a name="example"></a>範例

在下列範例中， `CUserView` 類別繼承自， `CWinFormsView` 並且將的型別傳遞至函式 `UserControl1` `CWinFormsView` 。 `UserControl1` 是 ControlLibrary1.dll 中的自訂建立控制項。

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

## <a name="cwinformsviewgetcontrol"></a><a name="getcontrol"></a> CWinFormsView::GetControl

抓取 Windows Forms 控制項的指標。

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>傳回值

`System.Windows.Forms.Control` 物件的指標。

### <a name="remarks"></a>備註

如需如何使用 Windows Forms 的範例，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="cwinformsviewoperator-control"></a><a name="operator_control"></a> CWinFormsView：： operator Control ^

將型別轉換為 Windows Forms 控制項的指標。

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>備註

這個運算子可讓您將 view 傳至函式 `CWinFormsView` ，以接受型別 Windows Forms 控制項的指標 <xref:System.Windows.Forms.Control> 。

### <a name="example"></a>範例

  請參閱 [CWinFormsView：： GetControl](#getcontrol)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl 類別](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog 類別](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView 類別](../../mfc/reference/cformview-class.md)
