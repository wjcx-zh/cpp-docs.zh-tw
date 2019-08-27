---
title: _U_MENUorID 類別
ms.date: 11/04/2016
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
ms.openlocfilehash: 9388ca1751ee27fb25d6751c961d23e5243f2918
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495137"
---
# <a name="_u_menuorid-class"></a>_U_MENUorID 類別

這個類別會提供和`CreateWindow` `CreateWindowEx`的包裝函式。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class _U_MENUorID
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|建構函式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|功能表的控制碼。|

## <a name="remarks"></a>備註

這個引數介面卡類別允許將識別碼 (UINTs) 或功能表控制碼 (HMENUs) 傳遞至函式, 而不需要在呼叫端的部分進行明確轉換。

這個類別是設計用來對 Windows API 執行包裝函式, 特別是[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww)和[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)函式, 兩者都接受可能是子視窗識別碼 (UINT) 而非功能表控制碼的 HMENU 引數。 例如, 您可以看到此類別做為[CWindowImpl:: Create](cwindowimpl-class.md#create)的參數使用。

類別會定義兩個函式多載: 一個會接受 UINT 引數, 另一個則接受 HMENU 引數。 UINT 引數只會轉換成函式中的 HMENU, 並將結果儲存在類別的單一資料成員[m_hMenu](#_u_menuorid__m_hmenu)中。 HMENU 函式的引數會直接儲存而不進行轉換。

## <a name="requirements"></a>需求

**標頭:** atlwin.h。h

##  <a name="_u_menuorid__m_hmenu"></a>_U_MENUorID::m_hMenu

類別會保存傳遞至其任何一個函式做為公用 HMENU 資料成員的值。

```
HMENU m_hMenu;
```

##  <a name="_u_menuorid___u_menuorid"></a>_U_MENUorID::_U_MENUorID

UINT 引數只會轉換成函式中的 HMENU, 並將結果儲存在類別的單一資料成員[m_hMenu](#_u_menuorid__m_hmenu)中。

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>參數

*nID*<br/>
子視窗識別碼。

*hMenu*<br/>
功能表控制碼。

### <a name="remarks"></a>備註

HMENU 函式的引數會直接儲存而不進行轉換。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
