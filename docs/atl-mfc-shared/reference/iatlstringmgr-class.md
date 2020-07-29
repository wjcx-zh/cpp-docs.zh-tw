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
ms.openlocfilehash: bee9c3d27ea05a40d6835d69079fc3e0a56efb86
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219049"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr 類別

此類別代表記憶體管理員的介面 `CStringT` 。

## <a name="syntax"></a>語法

```
__interface IAtlStringMgr
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[定位](#allocate)|呼叫這個方法來配置新的字串資料結構。|
|[複製](#clone)|呼叫這個方法，將指標傳回至新的字串管理員，以便與的另一個實例搭配使用 `CSimpleStringT` 。|
|[免費](#free)|呼叫這個方法以釋放字串資料結構。|
|[GetNilString](#getnilstring)|傳回 `CStringData` 空字串物件所使用之物件的指標。|
|[重新配置](#reallocate)|呼叫這個方法來重新配置字串資料結構。|

## <a name="remarks"></a>備註

這個介面會管理 MFC 獨立字串類別所使用的記憶體;例如[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)、 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)和[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)。

您也可以使用這個類別，為您的自訂字串類別實作為自訂記憶體管理員。 如需詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="requirements"></a>需求

**標頭：** atlsimpstr。h

## <a name="iatlstringmgrallocate"></a><a name="allocate"></a>IAtlStringMgr：： Allocate

配置新的字串資料結構。

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>參數

*nAllocLength*<br/>
新記憶體區塊中的字元數。

*nCharSize*<br/>
字串管理員所使用之字元類型的大小（以位元組為單位）。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊的指標。

> [!NOTE]
> 藉由擲回例外狀況，不要通知失敗的配置。 相反地，您應該傳回 Null 來通知失敗的配置。

### <a name="remarks"></a>備註

呼叫[IAtlStringMgr：： Free](#free)或[IAtlStringMgr：：](#reallocate)重新配置以釋放這個方法所配置的記憶體。

> [!NOTE]
> 如需使用範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrclone"></a><a name="clone"></a>IAtlStringMgr：： Clone

傳回新字串管理員的指標，以便與的另一個實例搭配使用 `CSimpleStringT` 。

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>傳回值

傳回 `IAtlStringMgr` 物件的複本。

### <a name="remarks"></a>備註

當新字串需要字串管理員時，通常是由架構所呼叫。 在大部分的情況下， **`this`** 會傳回指標。

不過，如果記憶體管理員不支援多個實例所使用的，則 `CSimpleStringT` 應該傳回可共用的字串管理員的指標。

> [!NOTE]
> 如需使用範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrfree"></a><a name="free"></a>IAtlStringMgr：： Free

釋放字串資料結構。

```cpp
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>參數

*pData*<br/>
要釋放的記憶體區塊指標。

### <a name="remarks"></a>備註

釋放先前配置[或重新](../../atl/reference/iatlmemmgr-class.md#reallocate)[配置所配置](#allocate)的指定記憶體區塊。

> [!NOTE]
> 如需使用範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrgetnilstring"></a><a name="getnilstring"></a>IAtlStringMgr::GetNilString

傳回空字串之字串資料結構的指標。

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>傳回值

物件的指標， `CStringData` 用來表示空字串。

### <a name="remarks"></a>備註

呼叫此函式可傳回空字串的標記法。

> [!NOTE]
> 在執行自訂字串管理員時，此函式永遠不會失敗。 您可以 `CNilStringData` 在字串管理員類別中內嵌實例，並傳回該實例的指標，以確保這點。

> [!NOTE]
> 如需使用範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="iatlstringmgrreallocate"></a><a name="reallocate"></a>IAtlStringMgr：：重新配置

重新配置字串資料結構。

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>參數

*pData*<br/>
此記憶體管理員先前所配置之記憶體的指標。

*nAllocLength*<br/>
新記憶體區塊中的字元數。

*nCharSize*<br/>
字串管理員所使用之字元類型的大小（以位元組為單位）。

### <a name="return-value"></a>傳回值

傳回新配置記憶體區塊開頭的指標。

### <a name="remarks"></a>備註

呼叫此函式可調整*pData*所指定的現有記憶體區塊大小。

呼叫[IAtlStringMgr：： free](#free)以釋放這個方法所配置的記憶體。

> [!NOTE]
> 如需使用範例，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
