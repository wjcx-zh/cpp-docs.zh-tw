---
title: CWndClassInfo 類別
ms.date: 11/04/2016
f1_keywords:
- CWndClassInfo
- ATLWIN/ATL::CWndClassInfo
- ATLWIN/ATL::Register
- ATLWIN/ATL::m_atom
- ATLWIN/ATL::m_bSystemCursor
- ATLWIN/ATL::m_lpszCursorID
- ATLWIN/ATL::m_lpszOrigName
- ATLWIN/ATL::m_szAutoName
- ATLWIN/ATL::m_wc
- ATLWIN/ATL::pWndProc
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
ms.openlocfilehash: 01706bf61c3b977c28998325ece68724cfbc7452
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330329"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo 類別

此類提供用於註冊視窗類資訊的方法。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CWndClassInfo
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|||
|-|-|
|[註冊](#register)|註冊視窗類。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_atom](#m_atom)|唯一標識已註冊的視窗類。|
|[m_bSystemCursor](#m_bsystemcursor)|指定游標資源是引用系統游標還是模組資源中包含的游標。|
|[m_lpszCursorID](#m_lpszcursorid)|指定游標資源的名稱。|
|[m_lpszOrigName](#m_lpszorigname)|包含現有視窗類的名稱。|
|[m_szAutoName](#m_szautoname)|保存視窗類的 ATL 生成名稱。|
|[m_wc](#m_wc)|在`WNDCLASSEX`結構中維護視窗類資訊。|
|[普恩德普羅克](#pwndproc)|指向現有視窗類的視窗過程。|

## <a name="remarks"></a>備註

`CWndClassInfo`管理視窗類的資訊。 通常通過三`CWndClassInfo`個宏之一(DECLARE_WND_CLASS、DECLARE_WND_CLASS_EX 或DECLARE_WND_SUPERCLASS)使用,如下表所述:

|巨集|描述|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo`註冊新視窗類的資訊。|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo`註冊新視窗類的資訊,包括類參數。|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo`註冊基於現有類但使用不同的視窗過程的視窗類的資訊。 此技術稱為超類。|

默認情況下[,CWindowImpl](../../atl/reference/cwindowimpl-class.md)包含`DECLARE_WND_CLASS`宏以基於新視窗類創建視窗。 DECLARE_WND_CLASS為控制項提供預設樣式和背景顏色。 如果要自己指定樣式和背景顏色,請從`CWindowImpl`類派生,並在類定義中包括DECLARE_WND_CLASS_EX宏。

如果要基於現有視窗類創建視窗,請從`CWindowImpl`類派生,並在類定義中包括DECLARE_WND_SUPERCLASS宏。 例如：

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

有關視窗類別詳細資訊,請參閱 Windows SDK 中的[視窗類別](/windows/win32/winmsg/window-classes)。

有關在 ATL 中使用視窗的詳細資訊,請參閱文章[ATL 視窗類別](../../atl/atl-window-classes.md)。

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="cwndclassinfom_atom"></a><a name="m_atom"></a>CWndClass資訊:m_atom

包含已註冊視窗類的唯一標識符。

```
ATOM m_atom;
```

## <a name="cwndclassinfom_bsystemcursor"></a><a name="m_bsystemcursor"></a>CWndClass資訊:m_bSystemCursor

如果為 TRUE,則在註冊視窗類時將載入系統游標資源。

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>備註

否則,將載入模組中包含的游標資源。

`CWndClassInfo`僅當`m_bSystemCursor`指定[DECLARE_WND_CLASS(CWindowImpl](../../atl/reference/cwindowimpl-class.md)中的預設值[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class))或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏時才使用。 在這種情況下,`m_bSystemCursor`將初始化為 TRUE。 有關詳細資訊,請參閱[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。

## <a name="cwndclassinfom_lpszcursorid"></a><a name="m_lpszcursorid"></a>CWndClassInfo:m_lpszCursorID

指定低階單詞中的游標資源的名稱或資源標識符,在高階單詞中指定零。

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>備註

註冊視窗類時,m_wc 檢索並存儲指向`m_lpszCursorID`標識的游標的句[m_wc](#m_wc)柄。

`CWndClassInfo`僅當`m_lpszCursorID`指定[DECLARE_WND_CLASS(CWindowImpl](../../atl/reference/cwindowimpl-class.md)中的預設值[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class))或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏時才使用。 在這種情況下,`m_lpszCursorID`將初始化為IDC_ARROW。 有關詳細資訊,請參閱[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。

## <a name="cwndclassinfom_lpszorigname"></a><a name="m_lpszorigname"></a>CWndClass資訊:m_lpszOrigName

包含現有視窗類的名稱。

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>備註

`CWndClassInfo`僅當`m_lpszOrigName`在類定義中包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏時才使用。 在這種情況下,`CWndClassInfo`根據`m_lpszOrigName`指定的類別的視窗類別。 有關詳細資訊,請參閱[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。

## <a name="cwndclassinfom_szautoname"></a><a name="m_szautoname"></a>CWndClass資訊:m_szAutoName

保存視窗類的名稱。

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>備註

`CWndClassInfo`只當`m_szAutoName`將`WndClassName`NULL 傳遞參數[以DECLARE_WND_CLASS、DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class)或[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)時,才使用 。 ATL 將在註冊視窗類時構造名稱。

## <a name="cwndclassinfom_wc"></a><a name="m_wc"></a>CWndClass資訊:m_wc

在[WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw)結構中維護視窗類資訊。

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>備註

`m_wc`如果指定[了](window-class-macros.md#declare_wnd_class)DECLARE_WND_CLASS(CWindowImpl[CWindowImpl](../../atl/reference/cwindowimpl-class.md)中的 預設值)或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏,則包含有關新視窗類的資訊。

如果指定了[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏`m_wc`,則 包含有關超類的資訊 - 一個基於現有類但使用不同的視窗過程的視窗類。 [m_lpszOrigName](#m_lpszorigname)和[pWndProc](#pwndproc)分別保存現有視窗類的名稱和視窗過程。

## <a name="cwndclassinfopwndproc"></a><a name="pwndproc"></a>CWndClassInfo::pWndProc

指向現有視窗類的視窗過程。

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>備註

`CWndClassInfo`僅當`pWndProc`在類定義中包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏時才使用。 在這種情況下,`CWndClassInfo`註冊基於現有類但使用不同的視窗過程的視窗類。 現有視窗類別的視窗存檔儲存在`pWndProc`中 。 有關詳細資訊,請參閱[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)概述。

## <a name="cwndclassinforegister"></a><a name="register"></a>CWndClassInfo::註冊

由[CWindowImpl 調用:創建](../../atl/reference/cwindowimpl-class.md#create)以註冊視窗類(如果尚未註冊)。

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>參數

*pProc*<br/>
[出]指定現有視窗類的原始視窗過程。

### <a name="return-value"></a>傳回值

如果成功,則唯一標識要註冊的視窗類的原子。 否則為 0。

### <a name="remarks"></a>備註

如果指定了`Register`[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)DECLARE_WND_CLASS(CWindowImpl[CWindowImpl](../../atl/reference/cwindowimpl-class.md)中的 預設值)或[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏,請註冊一個新的視窗類。 在這種情況下,不使用*pProc*參數。

如果指定了[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏`Register`,請註冊一個超級類 -一個基於現有類但使用不同的視窗過程的視窗類。 現有視窗類的視窗過程在*pProc*中返回。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
