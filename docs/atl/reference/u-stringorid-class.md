---
title: _U_STRINGorID類
ms.date: 11/04/2016
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
ms.openlocfilehash: 4e46ceec077b8daf8ef2a76110d2fc19dd39ae26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325816"
---
# <a name="_u_stringorid-class"></a>_U_STRINGorID類

此參數適配器類允許將資源名稱 (LPCTSTRs) 或資源 ID (UINT) 傳遞給函數,而無需呼叫者使用 MAKEINTRESOURCE 宏將 ID 轉換為字串。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class _U_STRINGorID
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[_U_STRINGorID:_U_STRINGorID](#_u_stringorid___u_stringorid)|建構函式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[_U_STRINGorID:m_lpstr](#_u_stringorid__m_lpstr)|資源標識符。|

## <a name="remarks"></a>備註

此類旨在實現 Windows 資源管理 API 的包裝器,如[FindResource、LoadIcon](/windows/win32/api/winbase/nf-winbase-findresourcea)和[LoadMenu](/windows/win32/api/winuser/nf-winuser-loadmenuw)函數,這些函數接受可以是資源名稱或其[LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)ID 的 LPCTSTR 參數。

該類定義兩個構造函數重載:一個接受 LPCTSTR 參數,另一個接受 UINT 參數。 UINT 參數將轉換為與 Windows 資源管理函數相容的資源類型,使用 MAKEINTRESOURCE 宏和存儲在類的單個資料成員m_lpstr[的結果。](#_u_stringorid__m_lpstr) LPCTSTR 構造函數的參數直接存儲而不轉換。

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="_u_stringoridm_lpstr"></a><a name="_u_stringorid__m_lpstr"></a>_U_STRINGorID:m_lpstr

類保存作為公共 LPCTSTR 數據成員傳遞給其任一構造函數的值。

```
LPCTSTR m_lpstr;
```

## <a name="_u_stringorid_u_stringorid"></a><a name="_u_stringorid___u_stringorid"></a>_U_STRINGorID:_U_STRINGorID

UINT 建構函式使用 MAKEINTRESOURCE 巨集將其參數轉換為與 Windows 資源管理函式相容的資源類型,結果儲存在類的單個資料成員[m_lpstr](#_u_stringorid__m_lpstr)。

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>參數

*nID*<br/>
資源識別碼。

*lpString*<br/>
資源名稱。

### <a name="remarks"></a>備註

LPCTSTR 構造函數的參數直接存儲而不轉換。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
