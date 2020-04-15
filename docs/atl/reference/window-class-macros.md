---
title: 視窗類巨集
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: 18c0912c506bc52421b18d36346204b557c0fc5c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325736"
---
# <a name="window-class-macros"></a>視窗類巨集

這些宏定義視窗類實用程式。

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|允許您指定新視窗類的名稱。|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(視覺工作室 2017)允許您指定新視窗類的名稱和封閉類的名稱,其視窗過程將使用新類。|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|允許您指定新視窗類將基於的現有視窗類的名稱。|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|允許您指定類的參數。|

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="declare_wnd_class"></a><a name="declare_wnd_class"></a>DECLARE_WND_CLASS

允許您指定新視窗類的名稱。 將此宏放在 ATL ActiveX 控制件的控制類中。

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>參數

*WndClass 名稱*<br/>
[在]新視窗類的名稱。 如果為 NULL,ATL 將生成視窗類名稱。

### <a name="remarks"></a>備註

如果使用 /允許編譯器選項,則DECLARE_WND_CLASS將導致編譯器錯誤;如果使用 /允許 - 編譯器選項,則DECLARE_WND_CLASS將導致編譯器錯誤。因此,DECLARE_WND_CLASS將會導致編譯器錯誤。改用DECLARE_WND_CLASS2。

DECLARE_WND_CLASS允許您指定一個新視窗類的名稱,其資訊將由[CWndClassInfo](cwndclassinfo-class.md)管理。 DECLARE_WND_CLASS通過以以下靜態函數來定義新的視窗類別:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS為新視窗指定以下樣式:

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS還指定預設視窗的背景顏色。 使用[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)宏提供您自己的樣式和背景顏色。

[CWindowImpl](cwindowimpl-class.md)使用DECLARE_WND_CLASS巨集基於新視窗類創建視窗。 要重寫此行為,請使用[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)宏,或提供您自己的[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函數的實現。

有關在 ATL 中使用視窗的詳細資訊,請參閱文章[ATL 視窗類別](../../atl/atl-window-classes.md)。

## <a name="declare_wnd_class2"></a><a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2

(視覺工作室 2017)類似於DECLARE_WND_CLASS,但具有一個額外的參數,在編譯 /允許選項時可以避免從屬名稱錯誤。

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>參數

*WndClass 名稱*<br/>
[在]新視窗類的名稱。 如果為 NULL,ATL 將生成視窗類名稱。

*封閉類*<br/>
[在]包含新視窗類的視窗類的名稱。 不能是 NULL。

### <a name="remarks"></a>備註

如果使用 /允許選項,則DECLARE_WND_CLASS將導致編譯錯誤,因為它包含從屬名稱。 DECLARE_WND_CLASS2要求您顯式命名此宏中使用的類,並且不會在 /允許 - 標誌下導致錯誤。
否則,此宏與[DECLARE_WND_CLASS](#declare_wnd_class)相同。

## <a name="declare_wnd_superclass"></a><a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS

允許您指定類的參數。 將此宏放在 ATL ActiveX 控制件的控制類中。

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>參數

*WndClass 名稱*<br/>
[在]將超類*OrigwndClassName*的視窗類別名稱。 如果為 NULL,ATL 將生成視窗類名稱。

*折元類別名稱*<br/>
[在]現有視窗類的名稱。

### <a name="remarks"></a>備註

此宏允許您指定將超類現有視窗類的視窗類的名稱。 [CWndClassInfo](cwndclassinfo-class.md)管理超類的資訊。

DECLARE_WND_SUPERCLASS實現以下靜態函數:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

默認情況下[,CWindowImpl](cwindowimpl-class.md)使用[DECLARE_WND_CLASS](#declare_wnd_class)宏基於新的視窗類創建視窗。 通過在`CWindowImpl`派生類中指定DECLARE_WND_SUPERCLASS宏,視窗類將基於現有類,但將使用視窗過程。 此技術稱為超類。

除了使用DECLARE_WND_CLASS和DECLARE_WND_SUPERCLASS宏外,您還可以使用自己的實現覆蓋[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函數。

有關在 ATL 中使用視窗的詳細資訊,請參閱文章[ATL 視窗類別](../../atl/atl-window-classes.md)。

## <a name="declare_wnd_class_ex"></a><a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX

允許您指定新視窗類將基於的現有視窗類的名稱。 將此宏放在 ATL ActiveX 控制件的控制類中。

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>參數

*WndClass 名稱*<br/>
[在]新視窗類的名稱。 如果為 NULL,ATL 將生成視窗類名稱。

*風格*<br/>
[在]視窗的樣式。

*布亨德*<br/>
[在]視窗的背景顏色。

### <a name="remarks"></a>備註

此宏允許您指定新視窗類的類參數,其資訊將由[CWndClassInfo](cwndclassinfo-class.md)管理。 DECLARE_WND_CLASS_EX通過使用以下靜態函數來定義新的視窗類別:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

如果要使用預設樣式和背景顏色,請使用[DECLARE_WND_CLASS](#declare_wnd_class)宏。 有關在 ATL 中使用視窗的詳細資訊,請參閱文章[ATL 視窗類別](../../atl/atl-window-classes.md)。

## <a name="see-also"></a>另請參閱

[巨集](atl-macros.md)
