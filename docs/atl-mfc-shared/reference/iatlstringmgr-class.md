---
title: IAtlStringMgr 類別
ms.date: 10/18/2018
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
ms.openlocfilehash: c3fabb7a7a6da4129787d219bd83b2a35fa0c4dd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746602"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr 類別

此類表示記憶體管理員的`CStringT`介面。

## <a name="syntax"></a>語法

```
__interface IAtlStringMgr
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[配置](#allocate)|呼叫此方法以分配新的字串資料結構。|
|[複製](#clone)|呼叫此方法傳回指向新字串管理員的指標,以便與另一個實體一`CSimpleStringT`起使用 。|
|[免費](#free)|呼叫此方法以釋放字串資料結構。|
|[獲得尼爾斯特林](#getnilstring)|返回指向空字串`CStringData`物件使用的物件的指標。|
|[重新分配](#reallocate)|呼叫此方法以重新分配字串資料結構。|

## <a name="remarks"></a>備註

此介面管理獨立於 MFC 的字串類使用的記憶體;例如[CSimpleStringT、CStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)與[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)。

您還可以使用此類實現自訂字串類的自定義記憶體管理員。 有關詳細資訊,請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="requirements"></a>需求

**標題:** atlsimpstr.h

## <a name="iatlstringmgrallocate"></a><a name="allocate"></a>IAtlStringMgr::分配

分配新的字串數據結構。

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>參數

*nAlloc 長度*<br/>
新記憶體區塊中的字元數。

*n字元*<br/>
字串管理器使用的字元類型的大小(以位元組為單位)。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊的指標。

> [!NOTE]
> 不要通過引發異常來發出分配失敗的信號。 相反,應返回 NULL 來發出失敗分配的信號。

### <a name="remarks"></a>備註

調用[IAtlStringMgr:免費](#free)或[IAtlStringMgr:重新分配](#reallocate)以釋放此方法分配的記憶體。

> [!NOTE]
> 有關使用範例,請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrclone"></a><a name="clone"></a>IAtlStringMgr:複製

傳回指向新字串管理員的指標,以便與的另一個`CSimpleStringT`實體一起使用 。

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>傳回值

傳回 `IAtlStringMgr` 物件的複本。

### <a name="remarks"></a>備註

當新字串需要字串管理器時,框架通常調用。 在大多數情況下,**將返回此**指標。

但是,如果記憶體管理員不支援由的`CSimpleStringT`多個實例使用,則應返回指向可共用字串管理器的指標。

> [!NOTE]
> 有關使用範例,請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrfree"></a><a name="free"></a>IAtlStringMgr:免費

釋放字串數據結構。

```cpp
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>參數

*pData*<br/>
指向要釋放的記憶體塊的指標。

### <a name="remarks"></a>備註

釋放以前由[分配](#allocate)或[重新分配](../../atl/reference/iatlmemmgr-class.md#reallocate)分配的指定記憶體區塊。

> [!NOTE]
> 有關使用範例,請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrgetnilstring"></a><a name="getnilstring"></a>IAtlStringMgr::GetNilString

返回指向空字串的字串資料結構的指標。

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>傳回值

指向用於表示空`CStringData`字串的物件的指標。

### <a name="remarks"></a>備註

呼叫此函數以返回空字串的表示形式。

> [!NOTE]
> 實現自定義字串管理器時,此函數絕不能失敗。 可以通過在字串管理器類中嵌入`CNilStringData`的 實例來確保這一點,並返回指向該實例的指標。

> [!NOTE]
> 有關使用範例,請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrreallocate"></a><a name="reallocate"></a>IAtlStringMgr:重新分配

重新分配字串數據結構。

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>參數

*pData*<br/>
指向以前由此記憶體管理器分配的記憶體的指標。

*nAlloc 長度*<br/>
新記憶體區塊中的字元數。

*n字元*<br/>
字串管理器使用的字元類型的大小(以位元組為單位)。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

呼叫此函數以調整*pData*指定的現有記憶體區塊的大小。

調用[IAtlStringMgr:可自由](#free)釋放此方法分配的記憶體。

> [!NOTE]
> 有關使用範例,請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
