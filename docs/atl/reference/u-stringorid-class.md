---
title: _U_STRINGorID 類別
ms.date: 11/04/2016
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
ms.openlocfilehash: c57d983e9680ce6d2cab375e427b80f4d3b6c2d6
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739571"
---
# <a name="_u_stringorid-class"></a>_U_STRINGorID 類別

這個引數介面卡類別允許將資源名稱（LPCTSTRs）或資源識別碼（UINTs）傳遞至函式，而不需要呼叫者使用 MAKEINTRESOURCE 宏將識別碼轉換成字串。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class _U_STRINGorID
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|建構函式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|資源識別碼。|

## <a name="remarks"></a>備註

這個類別是設計用來將包裝函式實作為 Windows 資源管理 API，例如[FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea)、 [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)和[LoadMenu](/windows/win32/api/winuser/nf-winuser-loadmenuw)函式，其接受的 LPCTSTR 引數可能是資源的名稱或識別碼。

類別會定義兩個函式多載：一個會接受 LPCTSTR 引數，另一個則接受 UINT 引數。 UINT 引數會轉換成與 Windows 資源管理函式相容的資源類型，使用 MAKEINTRESOURCE 宏和儲存在類別的單一資料成員[m_lpstr](#_u_stringorid__m_lpstr)中的結果。 LPCTSTR 函式的引數會直接儲存而不進行轉換。

## <a name="requirements"></a>需求

**標頭：** atlwin.h。h

##  <a name="_u_stringorid__m_lpstr"></a>_U_STRINGorID::m_lpstr

類別會保存傳遞至其任何一個函式做為公用 LPCTSTR 資料成員的值。

```
LPCTSTR m_lpstr;
```

##  <a name="_u_stringorid___u_stringorid"></a>_U_STRINGorID::_U_STRINGorID

UINT 處理常式會使用 MAKEINTRESOURCE 宏，將其引數轉換成與 Windows 資源管理函式相容的資源類型，並將結果儲存在類別的單一資料成員[m_lpstr](#_u_stringorid__m_lpstr)中。

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

LPCTSTR 函式的引數會直接儲存而不進行轉換。

## <a name="see-also"></a>另請參閱

[類別總覽](../../atl/atl-class-overview.md)
