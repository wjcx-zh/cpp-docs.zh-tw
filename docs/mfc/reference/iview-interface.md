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
ms.openlocfilehash: 22e08a70ff4cc742406a1489899c0ba1df7eb664
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78872442"
---
# <a name="iview-interface"></a>IView 介面

會執行數個[CWinFormsView](../../mfc/reference/cwinformsview-class.md)用來將視圖通知傳送至 managed 控制項的方法。

## <a name="syntax"></a>語法

```
interface class IView
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IView：： OnActivateView](#onactivateview)|當 view 已啟動或停用時，由 MFC 呼叫。|
|[IView：： OnInitialUpdate](#oninitialupdate)|在第一次將視圖附加至檔，但在一開始顯示視圖之前，由架構呼叫。|
|[IView：： OnUpdate](#onupdate)|在修改視圖的檔之後，由 MFC 呼叫;此函式可讓視圖更新其顯示以反映修改。|

## <a name="remarks"></a>備註

`IView` 會實 `CWinFormsView` 用來將常見視圖通知轉送至託管 managed 控制項的數種方法。 這些是[OnInitialUpdate](#oninitialupdate)、 [OnUpdate](#onupdate)和[OnActivateView](#onactivateview)。

`IView` 類似于[CView](../../mfc/reference/cview-class.md)，但只能搭配 managed 的視圖和控制項使用。

如需使用 Windows Forms 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="requirements"></a>需求

Header: afxwinforms.h (定義於組件 atlmfc\lib\mfcmifc80.dll)

## <a name="onactivateview"></a>IView：： OnActivateView

當 view 已啟動或停用時，由 MFC 呼叫。
```
void OnActivateView(bool activate);
```

## <a name="parameters"></a>參數

*啟用*<br/>
指出是否正在啟動或停用此視圖。

## <a name="oninitialupdate"></a>IView：： OnInitialUpdate

在第一次將視圖附加至檔，但在一開始顯示視圖之前，由架構呼叫。
```
void OnInitialUpdate();
```

## <a name="onupdate"></a>IView：： OnUpdate

在修改視圖的檔之後，由 MFC 呼叫。
```
void OnUpdate();
```

## <a name="remarks"></a>備註

此函式可讓視圖更新其顯示以反映修改。

## <a name="see-also"></a>另請參閱

[CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)
