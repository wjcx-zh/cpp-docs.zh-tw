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
ms.openlocfilehash: 9233ee5a8330c4b2c79ebc7b79e0616612c00204
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743421"
---
# <a name="iview-interface"></a>IView 介面

會實 [CWinFormsView](../../mfc/reference/cwinformsview-class.md) 用來將視圖通知傳送至 managed 控制項的數種方法。

## <a name="syntax"></a>語法

```
interface class IView
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IView：： OnActivateView](#onactivateview)|當啟用或停用 view 時，由 MFC 呼叫。|
|[IView：： OnInitialUpdate](#oninitialupdate)|在第一次將視圖附加至檔之後，但在第一次顯示視圖之前，由架構呼叫。|
|[IView：： OnUpdate](#onupdate)|在修改視圖檔之後由 MFC 呼叫;此函數可讓視圖更新其顯示，以反映修改。|

### <a name="remarks"></a>備註

`IView` 會執行數個方法，這些方法會 `CWinFormsView` 使用將一般視圖通知轉寄至裝載的 managed 控制項。 這些都是 [OnInitialUpdate](#oninitialupdate)、 [OnUpdate](#onupdate) 和 [OnActivateView](#onactivateview)。

`IView` 類似于 [CView](../../mfc/reference/cview-class.md)，但只能搭配 managed 視圖和控制項使用。

如需使用 Windows Forms 的詳細資訊，請參閱 [在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。

## <a name="requirements"></a>規格需求

Header: afxwinforms.h (定義於組件 atlmfc\lib\mfcmifc80.dll)

## <a name="iviewonactivateview"></a><a name="onactivateview"></a> IView：： OnActivateView

當啟用或停用 view 時，由 MFC 呼叫。

```cpp
void OnActivateView(bool activate);
```

## <a name="parameters"></a>參數

*啟用*<br/>
指出是否要啟用或停用此視圖。

## <a name="iviewoninitialupdate"></a><a name="oninitialupdate"></a> IView：： OnInitialUpdate

在第一次將視圖附加至檔之後，但在第一次顯示視圖之前，由架構呼叫。

```cpp
void OnInitialUpdate();
```

## <a name="iviewonupdate"></a><a name="onupdate"></a> IView：： OnUpdate

在修改視圖的檔之後，由 MFC 呼叫。

```cpp
void OnUpdate();
```

### <a name="remarks"></a>備註

此函數可讓視圖更新其顯示，以反映修改。

## <a name="see-also"></a>另請參閱

[CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)<br/>
[CView 類別](../../mfc/reference/cview-class.md)
