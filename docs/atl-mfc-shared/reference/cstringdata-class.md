---
title: CStringData 類別
ms.date: 11/04/2016
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
ms.openlocfilehash: f14f1d9c269f06099bd224f582de1f55da33ff0f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746833"
---
# <a name="cstringdata-class"></a>CStringData 類別

此類表示字串對象的數據。

## <a name="syntax"></a>語法

```
struct CStringData
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[AddRef](#addref)|增加字串資料物件的引用計數。|
|[資料](#data)|檢索字串物件的字元數據。|
|[IsLocked](#islocked)|確定關聯的字串對象的緩衝區是否鎖定。|
|[IsShared](#isshared)|確定關聯的字串對象的緩衝區當前是否共用。|
|[鎖](#lock)|鎖定關聯的字串對象的緩衝區。|
|[版本](#release)|釋放指定的字串物件。|
|[解除鎖定](#unlock)|解鎖關聯的字串對象的緩衝區。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[nAlloc 長度](#nalloclength)|S`XCHAR`中配置的資料(不包括終止 null)|
|[n 資料長度](#ndatalength)|s`XCHAR`中目前使用的資料長度(不包括終止 null)|
|[nRefs](#nrefs)|物件的當前引用計數。|
|[普斯特林姆格](#pstringmgr)|指向此字串物件的字串管理器的指標。|

## <a name="remarks"></a>備註

此類只能由實現自定義字串管理器的開發人員使用。 有關自訂字串管理員的詳細資訊,請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)

此類封裝了與較高字串物件(如[CStringT、CSimpleStringT](../../atl-mfc-shared/reference/cstringt-class.md)或[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)物件)關聯的各種類型的[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)資訊和數據。 每個較高的字串物件都包含指向其關聯`CStringData`物件的指標,允許多個字串物件指向同一字串數據物件。 此關係由`nRefs``CStringData`物件的引用計數 ( ) 表示。

> [!NOTE]
> 在某些情況下,字串類型(如`CFixedString`) 不會與多個較高字串物件共用字串數據物件。 有關此的詳細資訊,請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

此資料由:

- 字串的記憶體管理員[(IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)類型)。

- 字串的目前長度 ( [nData 長度](#ndatalength)) 。

- 字串的分配長度 ( [nAlloc 長度](#nalloclength)) 。 出於性能原因,這可能與當前字串長度不同

- `CStringData`物件的目前參考計數 ( [nRefs](#nrefs)) . 此值用於確定共用同一`CStringData`物件的字串物件數。

- 字串的實際字元緩衝區 ([資料](#data)) .

   > [!NOTE]
   > 字串對象的實際字元緩衝區由字串管理器分配並追加到該物件。 `CStringData`

## <a name="requirements"></a>需求

**標題:** atlsimpstr.h

## <a name="cstringdataaddref"></a><a name="addref"></a>弦資料::新增參考

增加字串物件的引用計數。

```cpp
void AddRef() throw();
```

### <a name="remarks"></a>備註

增加字串物件的引用計數。

> [!NOTE]
> 不要在具有負引用計數的字串上調用此方法,因為負計數表示字串緩衝區已鎖定。

## <a name="cstringdatadata"></a><a name="data"></a>弦樂資料::d

返回指向字串物件字元緩衝區的指標。

```cpp
void* data() throw();
```

### <a name="return-value"></a>傳回值

指向字串物件的字元緩衝區的指標。

### <a name="remarks"></a>備註

呼叫此函數以返回關聯字串物件的當前字元緩衝區。

> [!NOTE]
> 此緩衝區不是由物件分配,`CStringData`而是由字串管理器在需要時分配。 分配時,緩衝區將追加到字串數據物件。

## <a name="cstringdataislocked"></a><a name="islocked"></a>CStringData::鎖定

確定字元緩衝區是否鎖定。

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>傳回值

如果緩衝區已鎖定,則返回 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

呼叫此函數以確定字串物件的字元緩衝區當前是否鎖定。

## <a name="cstringdataisshared"></a><a name="isshared"></a>CStringData::共用

確定字元緩衝區是否共用。

```
bool IsShared() const throw();
```

### <a name="return-value"></a>傳回值

如果緩衝區是共用的,則返回 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

呼叫此函數以確定字串數據物件的字元緩衝區當前是否在多個字串對象之間共用。

## <a name="cstringdatalock"></a><a name="lock"></a>弦資料:鎖定

鎖定關聯字串物件的字元緩衝區。

```cpp
void Lock() throw();
```

### <a name="remarks"></a>備註

呼叫此函數以鎖定字串資料物件的字元緩衝區。 當開發人員需要直接存取字元緩衝區時,將使用鎖定和解鎖。 鎖定的一個好範例透過`CSimpleStringT`的[LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[解鎖緩衝區](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)方法演示。

> [!NOTE]
> 僅當緩衝區未在較高的字串對象之間共用時,才能鎖定字元緩衝區。

## <a name="cstringdatanalloclength"></a><a name="nalloclength"></a>CStringData::nAlloc長度

已分配的字元緩衝區的長度。

```
int nAllocLength;
```

### <a name="remarks"></a>備註

將分配的數據緩衝區的長度存儲在`XCHAR`s 中(不包括終止 null)。

## <a name="cstringdatandatalength"></a><a name="ndatalength"></a>CStringData:n數據長度

字串物件的當前長度。

```
int nDataLength;
```

### <a name="remarks"></a>備註

將目前使用的數據的長度儲存在`XCHAR`s 中(不包括終止 null)。

## <a name="cstringdatanrefs"></a><a name="nrefs"></a>CStringData::nRefs

字串資料物件的引用計數。

```
long nRefs;
```

### <a name="remarks"></a>備註

儲存字串資料物件的引用計數。 此計數指示與字串數據物件關聯的較高字串對象的數量。 負值表示字串數據物件當前已鎖定。

## <a name="cstringdatapstringmgr"></a><a name="pstringmgr"></a>弦樂數據::pStringMgr

關聯的字串物件的記憶體管理員。

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>備註

儲存關聯字串物件的記憶體管理員。 有關記憶體管理員和字串的詳細資訊,請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="cstringdatarelease"></a><a name="release"></a>CStringData::發佈

取消字串資料物件的引用計數。

```cpp
void Release() throw();
```

### <a name="remarks"></a>備註

調用此函數以遞減引用計數,在引用計數達到零`CStringData`時釋放結構。 這通常在刪除字串物件時完成,因此不再需要引用字串資料物件。

例如,以下代碼將調用`CStringData::Release`與關聯`str1`的字串數據物件。

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

## <a name="cstringdataunlock"></a><a name="unlock"></a>CStringData::解鎖

解鎖關聯的字串物件的字元緩衝區。

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>備註

呼叫此函數以解鎖字串資料物件的字元緩衝區。 一旦緩衝區解鎖,它是可共用的,可以進行引用計數。

> [!NOTE]
> 每個`Lock`調用都必須與相應的調用`Unlock`匹配。

當開發人員必須確保字串數據不共用時,將使用鎖定和解鎖。 鎖定的一個好範例透過`CSimpleStringT`的[LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)和[解鎖緩衝區](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)方法演示。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
