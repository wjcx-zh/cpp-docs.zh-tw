---
title: 視窗類別宏
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: c4617a04c199741b97316122456e417a94275e89
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862956"
---
# <a name="window-class-macros"></a>視窗類別宏

這些宏會定義 window 類別公用程式。

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|可讓您指定新視窗類別的名稱。|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|（Visual Studio 2017）可讓您指定新視窗類別的名稱，以及新類別將使用其視窗程式的封入類別。|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|可讓您指定現有視窗類別的名稱，新的視窗類別將以此為基礎。|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|可讓您指定類別的參數。|

## <a name="requirements"></a>需求

**標頭：** atlwin.h。h

##  <a name="declare_wnd_class"></a>DECLARE_WND_CLASS

可讓您指定新視窗類別的名稱。 將此宏放在 ATL ActiveX 控制項的控制項類別中。

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>參數

*WndClassName*<br/>
在新視窗類別的名稱。 如果是 Null，則 ATL 會產生視窗類別名稱。

### <a name="remarks"></a>備註

如果您使用/permissive-編譯器選項，則 DECLARE_WND_CLASS 會造成編譯器錯誤;請改用 DECLARE_WND_CLASS2。

DECLARE_WND_CLASS 可讓您指定新視窗類別的名稱，其資訊將由[CWndClassInfo](cwndclassinfo-class.md)管理。 DECLARE_WND_CLASS 藉由執行下列靜態函式來定義新的視窗類別：

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS 指定新視窗的下列樣式：

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS 也會指定預設視窗的背景色彩。 使用[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)宏來提供您自己的樣式和背景色彩。

[CWindowImpl](cwindowimpl-class.md)會使用 DECLARE_WND_CLASS 宏，根據新的視窗類別來建立視窗。 若要覆寫此行為，請使用[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)宏，或提供您自己的[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函式實作為。

如需在 ATL 中使用視窗的詳細資訊，請參閱[Atl 視窗類別](../../atl/atl-window-classes.md)一文。

##  <a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2

（Visual Studio 2017）類似于 DECLARE_WND_CLASS，但具有額外的參數，可在使用/permissive-選項編譯時避免相依名稱錯誤。

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>參數

*WndClassName*<br/>
在新視窗類別的名稱。 如果是 Null，則 ATL 會產生視窗類別名稱。

*EnclosingClass*<br/>
在括住新視窗類別的視窗類別名稱。 不能是 NULL。

### <a name="remarks"></a>備註

如果您使用/permissive-選項，DECLARE_WND_CLASS 將會造成編譯錯誤，因為它包含相依名稱。 DECLARE_WND_CLASS2 需要您明確命名用來使用此宏的類別，而且不會在/permissive-旗標底下造成錯誤。
否則，這個宏就等同于[DECLARE_WND_CLASS](#declare_wnd_class)。

##  <a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS

可讓您指定類別的參數。 將此宏放在 ATL ActiveX 控制項的控制項類別中。

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>參數

*WndClassName*<br/>
在將會*OrigWndClassName*超級類別的視窗類別名稱。 如果是 Null，則 ATL 會產生視窗類別名稱。

*OrigWndClassName*<br/>
在現有視窗類別的名稱。

### <a name="remarks"></a>備註

這個宏可讓您指定將現有視窗類別設為超級類別的視窗類別名稱。 [CWndClassInfo](cwndclassinfo-class.md)會管理超級類別的資訊。

DECLARE_WND_SUPERCLASS 會實作用下列靜態函式：

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

根據預設， [CWindowImpl](cwindowimpl-class.md)會使用[DECLARE_WND_CLASS](#declare_wnd_class)宏來建立以新視窗類別為基礎的視窗。 藉由在 `CWindowImpl`衍生類別中指定 DECLARE_WND_SUPERCLASS 宏，視窗類別將會以現有的類別為基礎，但會使用您的視窗程式。 這項技術稱為 superclassing。

除了使用 DECLARE_WND_CLASS 和 DECLARE_WND_SUPERCLASS 宏之外，您還可以使用自己的執行覆寫[GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo)函式。

如需在 ATL 中使用視窗的詳細資訊，請參閱[Atl 視窗類別](../../atl/atl-window-classes.md)一文。

##  <a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX

可讓您指定現有視窗類別的名稱，新的視窗類別將以此為基礎。 將此宏放在 ATL ActiveX 控制項的控制項類別中。

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>參數

*WndClassName*<br/>
在新視窗類別的名稱。 如果是 Null，則 ATL 會產生視窗類別名稱。

*style*<br/>
在視窗的樣式。

*bkgnd*<br/>
在視窗的背景色彩。

### <a name="remarks"></a>備註

這個宏可讓您指定新視窗類別的類別參數，其資訊將由[CWndClassInfo](cwndclassinfo-class.md)管理。 DECLARE_WND_CLASS_EX 藉由執行下列靜態函式來定義新的視窗類別：

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

如果您想要使用預設樣式和背景色彩，請使用[DECLARE_WND_CLASS](#declare_wnd_class)宏。 如需在 ATL 中使用視窗的詳細資訊，請參閱[Atl 視窗類別](../../atl/atl-window-classes.md)一文。

## <a name="see-also"></a>另請參閱

[巨集](atl-macros.md)
