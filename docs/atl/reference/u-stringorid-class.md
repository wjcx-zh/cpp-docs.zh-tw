---
title: _U_STRINGorID 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
dev_langs:
- C++
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 000e43926a83bdd7457c33c656383ae44dce6259
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046273"
---
# <a name="ustringorid-class"></a>_U_STRINGorID 類別

資源名稱 (LPCTSTRs)] 或 [資源識別碼 （所） 傳遞至函式，而不需要呼叫者識別碼轉換為使用 MAKEINTRESOURCE 巨集的字串，可讓這個引數的配接器類別。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class _U_STRINGorID
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|建構函式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|資源識別項。|

## <a name="remarks"></a>備註

這個類別專為這類實作的 Windows 資源管理 API 的包裝函式[FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea)， [LoadIcon](/windows/desktop/api/winuser/nf-winuser-loadicona)，並[LoadMenu](/windows/desktop/api/winuser/nf-winuser-loadmenua)函式，可接受可能是資源的名稱或識別碼為 LPCTSTR 引數

此類別會定義兩個建構函式多載︰ 一個接受 LPCTSTR 引數和一個接受 UINT 引數。 UINT 引數會轉換成相容於使用 MAKEINTRESOURCE 巨集和結果儲存在該類別的單一資料成員的 Windows 資源管理函式的資源類型[m_lpstr](#_u_stringorid__m_lpstr)。 轉換不直接儲存 LPCTSTR 建構函式的引數。

## <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="_u_stringorid__m_lpstr"></a>  _U_STRINGorID::m_lpstr

類別包含傳遞至其建構函式做為公用的 LPCTSTR 資料成員的值。

```
LPCTSTR m_lpstr;
```

##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID

UINT 建構函式會將其引數轉換成相容於 Windows 資源管理函式使用 MAKEINTRESOURCE 巨集的資源類型，並將結果儲存在該類別的單一資料成員中， [m_lpstr](#_u_stringorid__m_lpstr)。

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

轉換不直接儲存 LPCTSTR 建構函式的引數。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
