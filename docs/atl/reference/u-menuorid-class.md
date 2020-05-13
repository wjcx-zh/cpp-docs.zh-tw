---
title: _U_MENUorID類
ms.date: 11/04/2016
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
ms.openlocfilehash: 419c9e79178db12efe278838ec8630e04ac3c461
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325829"
---
# <a name="_u_menuorid-class"></a>_U_MENUorID類

此類為`CreateWindow`和`CreateWindowEx`提供包裝。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class _U_MENUorID
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[_U_MENUorID:_U_MENUorID](#_u_menuorid___u_menuorid)|建構函式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[_U_MENUorID:m_hMenu](#_u_menuorid__m_hmenu)|功能表的句柄。|

## <a name="remarks"></a>備註

此參數適配器類允許將 ID (UINTs) 或功能表句柄 (HMENUs) 傳遞給函數,而無需調用方的顯式強制轉換。

此類旨在實現 Windows API 的包裝,尤其是[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww)和[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)函數,這兩個函數都接受可能是子窗口識別碼 (UINT) 而不是功能表句柄的 HMENU 參數。 例如,您可以看到此類正在用作[CWindowImpl:::create](cwindowimpl-class.md#create)的參數。

類定義兩個構造函數重載:一個接受 UINT 參數,另一個接受 HMENU 參數。 UINT 參數只是強制轉換為建構函數中的 HMENU,並將結果存儲在類的單個數據成員[m_hMenu](#_u_menuorid__m_hmenu)中。 HMENU 建構函數的參數直接存儲而不轉換。

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="_u_menuoridm_hmenu"></a><a name="_u_menuorid__m_hmenu"></a>_U_MENUorID:m_hMenu

類保存作為公共 HMENU 數據成員傳遞給其任一構造函數的值。

```
HMENU m_hMenu;
```

## <a name="_u_menuorid_u_menuorid"></a><a name="_u_menuorid___u_menuorid"></a>_U_MENUorID:_U_MENUorID

UINT 參數只是強制轉換為建構函數中的 HMENU,並將結果存儲在類的單個數據成員[m_hMenu](#_u_menuorid__m_hmenu)中。

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>參數

*nID*<br/>
子窗口識別碼。

*hMenu*<br/>
功能表句柄。

### <a name="remarks"></a>備註

HMENU 建構函數的參數直接存儲而不轉換。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
