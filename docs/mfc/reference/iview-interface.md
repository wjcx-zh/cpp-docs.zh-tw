---
title: IView 介面
ms.date: 11/04/2016
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
ms.openlocfilehash: dfe77699a51ad2670c703d02e13e9062e76debcd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751290"
---
# <a name="iview-interface"></a>IView 介面

實現[CWinFormsView](../../mfc/reference/cwinformsview-class.md)用於向託管控件發送視圖通知的幾種方法。

## <a name="syntax"></a>語法

```
interface class IView
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IView:開啟啟動檢視](#onactivateview)|當視圖啟動或停用時,MFC 調用。|
|[IView::初始更新](#oninitialupdate)|視圖首次附加到文檔後由框架調用,但在最初顯示視圖之前。|
|[IView::更新](#onupdate)|修改檢視文檔後由 MFC 調用;此功能允許檢視更新其顯示以反映修改。|

## <a name="remarks"></a>備註

`IView`實作幾種方法`CWinFormsView`, 用於將公共檢視通知轉發到託管託管託管管理。 這些是[「初始更新](#oninitialupdate)[」、「更新」](#onupdate)和[「啟動檢視](#onactivateview)」 。

`IView`與[CView](../../mfc/reference/cview-class.md)類似,但僅用於託管視圖和控制項。

有關使用 Windows 表單的詳細資訊,請參閱[在 MFC 中使用 Windows 元件使用者控制件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="requirements"></a>需求

Header: afxwinforms.h (定義於組件 atlmfc\lib\mfcmifc80.dll)

## <a name="iviewonactivateview"></a><a name="onactivateview"></a>IView:開啟啟動檢視

當視圖啟動或停用時,MFC 調用。

```cpp
void OnActivateView(bool activate);
```

## <a name="parameters"></a>參數

*啟用*<br/>
指示視圖是正在啟動還是停用。

## <a name="iviewoninitialupdate"></a><a name="oninitialupdate"></a>IView::初始更新

視圖首次附加到文檔後由框架調用,但在最初顯示視圖之前。

```cpp
void OnInitialUpdate();
```

## <a name="iviewonupdate"></a><a name="onupdate"></a>IView::更新

修改檢視文檔後由 MFC 調用。

```cpp
void OnUpdate();
```

## <a name="remarks"></a>備註

此功能允許檢視更新其顯示以反映修改。

## <a name="see-also"></a>另請參閱

[CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)
