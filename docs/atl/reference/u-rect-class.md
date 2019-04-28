---
title: _U_RECT 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
ms.openlocfilehash: 306092a00a1e119263f4563eea181d7d3ee2b4b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274521"
---
# <a name="urect-class"></a>_U_RECT 類別

這個引數的配接器類別可讓`RECT`指標或參考傳遞至函式實作方面的指標。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class _U_RECT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|建構函式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|指標`RECT`。|

## <a name="remarks"></a>備註

此類別會定義兩個建構函式多載： 其中一個接受**RECT &** 引數，而另一個接受`LPRECT`引數。 第一個建構函式會參考引數的位址儲存在該類別的單一資料成員中， [m_lpRect](#_u_rect__m_lprect)。 轉換不直接儲存的指標建構函式的引數。

## <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="_u_rect__m_lprect"></a>  _U_RECT::m_lpRect

類別會保存的值傳遞至其建構函式為公用`LPRECT`資料成員。

```
LPRECT m_lpRect;
```

##  <a name="_u_rect___u_rect"></a>  _U_RECT::_U_RECT

參考引數的位址儲存在該類別的單一資料成員中， [m_lpRect](#_u_rect__m_lprect)。

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>參數

*rc*<br/>
A`RECT`參考。

*lpRect*<br/>
A`RECT`指標。

### <a name="remarks"></a>備註

轉換不直接儲存的指標建構函式的引數。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
