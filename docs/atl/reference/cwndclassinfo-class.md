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
ms.openlocfilehash: c1b516f6e92f98d660f7757870a3e634dcef4518
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835502"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo 類別

這個類別提供註冊視窗類別資訊的方法。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式中，無法使用這個類別和其成員。

## <a name="syntax"></a>語法

```
class CWndClassInfo
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|-|-|
|[註冊](#register)|註冊視窗類別。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|-|-|
|[m_atom](#m_atom)|唯一識別已註冊的視窗類別。|
|[m_bSystemCursor](#m_bsystemcursor)|指定資料指標資源是指系統資料指標或包含在模組資源中的資料指標。|
|[m_lpszCursorID](#m_lpszcursorid)|指定資料指標資源的名稱。|
|[m_lpszOrigName](#m_lpszorigname)|包含現有視窗類別的名稱。|
|[m_szAutoName](#m_szautoname)|保存由 ATL 產生的視窗類別名稱。|
|[m_wc](#m_wc)|在結構中維護視窗類別資訊 `WNDCLASSEX` 。|
|[pWndProc](#pwndproc)|指向現有視窗類別的視窗程式。|

## <a name="remarks"></a>備註

`CWndClassInfo` 管理視窗類別的資訊。 您通常會使用 `CWndClassInfo` 三個宏的其中一種，DECLARE_WND_CLASS、DECLARE_WND_CLASS_EX 或 DECLARE_WND_SUPERCLASS，如下表所述：

|巨集|描述|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo` 註冊新視窗類別的資訊。|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo` 註冊新視窗類別的資訊，包括類別參數。|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo` 註冊以現有類別為基礎但使用不同視窗程式之視窗類別的資訊。 這項技術稱為 superclassing。|

根據預設， [CWindowImpl](../../atl/reference/cwindowimpl-class.md) 會包含 `DECLARE_WND_CLASS` 宏，以根據新的視窗類別來建立視窗。 DECLARE_WND_CLASS 提供控制項的預設樣式和背景色彩。 如果您想要自行指定樣式和背景色彩，請從衍生類別， `CWindowImpl` 並在類別定義中包含 DECLARE_WND_CLASS_EX 宏。

如果您想要根據現有的視窗類別建立視窗，請從衍生類別， `CWindowImpl` 並在類別定義中包含 DECLARE_WND_SUPERCLASS 宏。 例如：

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

如需視窗類別的詳細資訊，請參閱 Windows SDK 中的 [視窗類別](/windows/win32/winmsg/window-classes) 。

如需有關在 ATL 中使用 windows 的詳細資訊，請參閱 [Atl 視窗類別](../../atl/atl-window-classes.md)一文。

## <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="cwndclassinfom_atom"></a><a name="m_atom"></a> CWndClassInfo：： m_atom

包含已註冊視窗類別的唯一識別碼。

```
ATOM m_atom;
```

## <a name="cwndclassinfom_bsystemcursor"></a><a name="m_bsystemcursor"></a> CWndClassInfo：： m_bSystemCursor

若為 TRUE，則會在註冊視窗類別時載入系統資料指標資源。

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>備註

否則，將會載入模組中包含的資料指標資源。

`CWndClassInfo``m_bSystemCursor`只有在[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) ([CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 中的預設值，或指定[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏時，才會使用。 在此情況下， `m_bSystemCursor` 會初始化為 TRUE。 如需詳細資訊，請參閱 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) 總覽。

## <a name="cwndclassinfom_lpszcursorid"></a><a name="m_lpszcursorid"></a> CWndClassInfo：： m_lpszCursorID

指定資料指標資源的名稱或低序位單字中的資源識別碼，以及高序位單字中的零。

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>備註

註冊視窗類別之後， `m_lpszCursorID` [m_wc](#m_wc)會抓取和儲存所識別之資料指標的控制碼。

`CWndClassInfo``m_lpszCursorID`只有在[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) ([CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 中的預設值，或指定[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)宏時，才會使用。 在此情況下， `m_lpszCursorID` 會初始化為 IDC_ARROW。 如需詳細資訊，請參閱 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) 總覽。

## <a name="cwndclassinfom_lpszorigname"></a><a name="m_lpszorigname"></a> CWndClassInfo：： m_lpszOrigName

包含現有視窗類別的名稱。

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>備註

`CWndClassInfo``m_lpszOrigName`只有當您在類別定義中包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏時，才會使用。 在此情況下，會 `CWndClassInfo` 根據名為的類別來註冊視窗類別 `m_lpszOrigName` 。 如需詳細資訊，請參閱 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) 總覽。

## <a name="cwndclassinfom_szautoname"></a><a name="m_szautoname"></a> CWndClassInfo：： m_szAutoName

保存視窗類別的名稱。

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>備註

`CWndClassInfo``m_szAutoName`只有在傳遞 Null 給 `WndClassName` 參數以[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)、 [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)或[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)時，才會使用。 當註冊視窗類別時，ATL 會建立名稱。

## <a name="cwndclassinfom_wc"></a><a name="m_wc"></a> CWndClassInfo：： m_wc

在 [WNDCLASSEX](/windows/win32/api/winuser/ns-winuser-wndclassexw) 結構中維護視窗類別資訊。

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>備註

如果您已指定 [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) ([CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或 [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) 宏中的預設值，則會 `m_wc` 包含新視窗類別的相關資訊。

如果您已指定 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 宏，則 `m_wc` 會包含一個超級類別的相關資訊，此視窗類別是以現有類別為基礎，但使用不同的視窗程式。 [m_lpszOrigName](#m_lpszorigname) 和 [pWndProc](#pwndproc) 會分別儲存現有的視窗類別的名稱和視窗程式。

## <a name="cwndclassinfopwndproc"></a><a name="pwndproc"></a> CWndClassInfo：:p WndProc

指向現有視窗類別的視窗程式。

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>備註

`CWndClassInfo``pWndProc`只有當您在類別定義中包含[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)宏時，才會使用。 在此情況下， `CWndClassInfo` 會根據現有的類別註冊視窗類別，但使用不同的視窗程式。 現有視窗類別的視窗程式會儲存在中 `pWndProc` 。 如需詳細資訊，請參閱 [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) 總覽。

## <a name="cwndclassinforegister"></a><a name="register"></a> CWndClassInfo：： Register

呼叫 [CWindowImpl：： Create](../../atl/reference/cwindowimpl-class.md#create) 以註冊視窗類別（如果尚未註冊的話）。

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>參數

*pProc*<br/>
擴展指定現有視窗類別的原始視窗程式。

### <a name="return-value"></a>傳回值

如果成功，則為可唯一識別要註冊之視窗類別的 atom。 否則為 0。

### <a name="remarks"></a>備註

如果您已指定 [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) ([CWindowImpl](../../atl/reference/cwindowimpl-class.md)) 或 [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) 宏中的預設值，則會 `Register` 註冊新的視窗類別。 在此情況下，不會使用 *pProc* 參數。

如果您已指定 [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) 宏，則 `Register` 會註冊一個超類別（以現有類別為基礎的視窗類別），但會使用不同的視窗程式。 現有視窗類別的視窗程式會在 *pProc*中傳回。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
