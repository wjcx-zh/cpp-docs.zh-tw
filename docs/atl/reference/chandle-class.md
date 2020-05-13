---
title: CHandle 類別
ms.date: 07/09/2019
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
ms.openlocfilehash: 4b883bdf3159c40f8d74866f04f655ae73d82a8a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747691"
---
# <a name="chandle-class"></a>CHandle 類別

此類提供了創建和使用句柄物件的方法。

## <a name="syntax"></a>語法

```
class CHandle
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[操作::CHandle](#chandle)|建構函式。|
|[操作::*CHandle](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[操作::附加](#attach)|調用此方法將`CHandle`物件附加到現有句柄。|
|[操作:關閉](#close)|呼叫此方法以關閉物件`CHandle`。|
|[查德::D塔奇](#detach)|調用此方法以從`CHandle`物件分離句柄。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[操作::操作員操作](#operator_handle)|返回存儲句柄的值。|
|[操作::運算符 |](#operator_eq)|指派運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[操作::m_h](#m_h)|存儲句柄的成員變數。|

## <a name="remarks"></a>備註

每當`CHandle`需要句柄時,都可以使用物件:主要區別是該`CHandle`物件將自動刪除。

> [!NOTE]
> 某些 API 函數將使用 NULL 作為空句柄或無效句柄,而其他函數則使用INVALID_HANDLE_VALUE。 `CHandle`僅使用 NULL,並將INVALID_HANDLE_VALUE視為真正的句柄。 如果調用可以返回INVALID_HANDLE_VALUE的 API,則應在調用[CHandle::附加](#attach)`CHandle`或傳遞給 構造函數之前檢查此值,然後傳遞 NULL。

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="chandleattach"></a><a name="attach"></a>操作::附加

調用此方法將`CHandle`物件附加到現有句柄。

```cpp
void Attach(HANDLE h) throw();
```

### <a name="parameters"></a>參數

*H*<br/>
`CHandle`將取得句柄*h*的擁有權。

### <a name="remarks"></a>備註

將`CHandle`物件配置給*h*句柄,然後呼叫**h.detach()**。 在除錯產生中,如果*h*為 NULL,將引發 ATLASSERT。 沒有對手柄的有效性進行其他檢查。

## <a name="chandlechandle"></a><a name="chandle"></a>操作::CHandle

建構函式。

```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```

### <a name="parameters"></a>參數

*H*<br/>
現有句柄`CHandle`或 。

### <a name="remarks"></a>備註

創建新`CHandle`物件,可以選擇使用現有句柄`CHandle`或 物件。

## <a name="chandlechandle"></a><a name="dtor"></a>操作::*CHandle

解構函式。

```
~CHandle() throw();
```

### <a name="remarks"></a>備註

通過調用`CHandle`[CHandle::關閉](#close)來釋放物件。

## <a name="chandleclose"></a><a name="close"></a>操作:關閉

呼叫此方法以關閉物件`CHandle`。

```cpp
void Close() throw();
```

### <a name="remarks"></a>備註

關閉打開的物件句柄。 如果句柄為 NULL(`Close`如果已呼叫,則為 NULL,則將在調試生成中引發 ATLASSERT)。

## <a name="chandledetach"></a><a name="detach"></a>查德::D塔奇

調用此方法以從`CHandle`物件分離句柄。

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>傳回值

返回要分離的句柄。

### <a name="remarks"></a>備註

釋放句柄的擁有權。

## <a name="chandlem_h"></a><a name="m_h"></a>操作::m_h

存儲句柄的成員變數。

```
HANDLE m_h;
```

## <a name="chandleoperator-"></a><a name="operator_eq"></a>操作::運算符 |

分配運算符。

```
CHandle& operator=(CHandle& h) throw();
```

### <a name="parameters"></a>參數

*H*<br/>
`CHandle`將取得句柄*h*的擁有權。

### <a name="return-value"></a>傳回值

返回對新`CHandle`物件的引用。

### <a name="remarks"></a>備註

如果`CHandle`物件當前包含句柄,它將關閉。 傳入`CHandle`的物件的句柄引用集 NULL。 這可確保兩`CHandle`個對象永遠不會包含相同的活動句柄。

## <a name="chandleoperator-handle"></a><a name="operator_handle"></a>操作::操作員操作

返回存儲句柄的值。

```
operator HANDLE() const throw();
```

### <a name="remarks"></a>備註

返回存儲在[CHandle::m_h](#m_h)中的值。

## <a name="see-also"></a>另請參閱

[類別概觀](../../atl/atl-class-overview.md)
