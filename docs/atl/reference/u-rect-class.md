---
title: _U_RECT類
ms.date: 11/04/2016
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
ms.openlocfilehash: 8a4d5b2a770b3f0ecfe10be0fbad22a702aa0531
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325815"
---
# <a name="_u_rect-class"></a>_U_RECT類

此參數適配器類允許將`RECT`指標或引用傳遞給在指標方面實現的函數。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class _U_RECT
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[_U_RECT:_U_RECT](#_u_rect___u_rect)|建構函式。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[_U_RECT:m_lpRect](#_u_rect__m_lprect)|指向的`RECT`指標。|

## <a name="remarks"></a>備註

類定義兩個構造函數重載:一個接受**RECT&** 參數,`LPRECT`另一個 接受參數。 第一個建構函數將引用參數的位址儲存在類的單個資料成員[m_lpRect](#_u_rect__m_lprect)。 指標構造函數的參數直接存儲而不轉換。

## <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="_u_rectm_lprect"></a><a name="_u_rect__m_lprect"></a>_U_RECT:m_lpRect

類保存作為公共`LPRECT`數據成員傳遞給其任一構造函數的值。

```
LPRECT m_lpRect;
```

## <a name="_u_rect_u_rect"></a><a name="_u_rect___u_rect"></a>_U_RECT:_U_RECT

參考參數的位址儲存在類別的單個資料成員[中,m_lpRect](#_u_rect__m_lprect)。

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>參數

*鋼筋混凝土*<br/>
`RECT` 參考。

*lpRect*<br/>
指標`RECT`。

### <a name="remarks"></a>備註

指標構造函數的參數直接存儲而不轉換。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
