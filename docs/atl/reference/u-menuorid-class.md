---
title: _U_MENUorID 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
dev_langs:
- C++
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e5902019704821d6c34c74480623593b7d7448a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044245"
---
# <a name="umenuorid-class"></a>_U_MENUorID 類別

這個類別會提供包裝函式`CreateWindow`和`CreateWindowEx`。

> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。

## <a name="syntax"></a>語法

```
class _U_MENUorID
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|建構函式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|功能表控制代碼。|

## <a name="remarks"></a>備註

這個引數的配接器類別會允許呼叫端執行識別碼 （所） 或功能表控制代碼 (HMENUs) 傳遞至函式，而不需要明確轉換。

這個類別專為實作包裝函式以 Windows API 中，特別[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa)並[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)函式，這兩者都接受 HMENU 引數可能是子視窗識別碼 (UINT)，而非功能表控制代碼。 例如，您可以看到在使用這個類別做為參數[CWindowImpl::Create](cwindowimpl-class.md#create)。  

此類別會定義兩個建構函式多載︰ 一個接受 UINT 引數和其他接受 HMENU 引數。 UINT 引數只會轉換成建構函式和儲存類別的單一資料成員，在結果中的 HMENU [m_hMenu](#_u_menuorid__m_hmenu)。 轉換不直接儲存的 HMENU 建構函式的引數。

## <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="_u_menuorid__m_hmenu"></a>  _U_MENUorID::m_hMenu

類別包含傳遞至其建構函式做為公用的 HMENU 資料成員的值。

```
HMENU m_hMenu;
```

##  <a name="_u_menuorid___u_menuorid"></a>  _U_MENUorID::_U_MENUorID

UINT 引數只會轉換成建構函式和儲存類別的單一資料成員，在結果中的 HMENU [m_hMenu](#_u_menuorid__m_hmenu)。

```
_U_MENUorID(UINT nID);
_U_MENUorID(HMENU hMenu);
```

### <a name="parameters"></a>參數

*nID*<br/>
子視窗識別碼。

*hMenu*<br/>
功能表控制代碼。

### <a name="remarks"></a>備註

轉換不直接儲存的 HMENU 建構函式的引數。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
