---
title: CStringData 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: effc4166fa25cec03ea62a5dd35a5396d2d2a3f2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419785"
---
# <a name="cstringdata-class"></a>CStringData 類別

此類別代表的字串物件的資料。

## <a name="syntax"></a>語法

```
struct CStringData
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[AddRef](#addref)|字串資料物件的參考計數會遞增。|
|[data](#data)|擷取字元資料的字串物件。|
|[IsLocked](#islocked)|決定是否鎖定相關聯的 string 物件的緩衝區。|
|[IsShared](#isshared)|決定是否相關聯的 string 物件的緩衝區目前的共用。|
|[鎖定](#lock)|鎖定相關聯的 string 物件的緩衝區。|
|[發行](#release)|釋放指定的字串物件。|
|[解除鎖定](#unlock)|解除鎖定相關聯的 string 物件的緩衝區。|

### <a name="data-members"></a>資料成員

|||
|-|-|
|[nAllocLength](#nalloclength)|配置中的資料長度`XCHAR`s （不含終止 null)|
|[nDataLength](#ndatalength)|目前使用中的資料長度`XCHAR`s （不含終止 null)|
|[nRefs](#nrefs)|物件的目前參考計數。|
|[pStringMgr](#pstringmgr)|字串管理員，這個字串物件的指標。|

## <a name="remarks"></a>備註

此類別僅供開發人員實作自訂字串管理員。 如需有關自訂字串管理員的詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)

這個類別會封裝各種類型的資訊和資料與較高的字串物件，例如相關聯[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)， [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)，或[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)物件。 每個更新版本的字串物件包含與其相關聯的指標`CStringData`物件，讓多個指向相同的字串資料物件的字串物件。 此關聯性由參考計數 (`nRefs`) 的`CStringData`物件。

> [!NOTE]
>  在某些情況下，字串型別 (例如`CFixedString`) 將不會與多個更新版本的字串物件共用的字串資料物件。 如需詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

包含此資料：

- 記憶體管理員 (型別的[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) 的字串。

- 目前的長度 ( [nDataLength](#ndatalength)) 的字串。

- 已配置的長度 ( [nAllocLength](#nalloclength)) 的字串。 基於效能考量，這可能不同於目前字串的長度

- 目前的參考計數 ( [nRefs](#nrefs)) 的`CStringData`物件。 這個值會用於決定多少字串物件會共用相同`CStringData`物件。

- 實際的字元緩衝區 ([資料](#data)) 的字串。

   > [!NOTE]
   > 實際的字元緩衝區的字串物件由字串管理員所配置，並附加至`CStringData`物件。

## <a name="requirements"></a>需求

**標頭：** atlsimpstr.h

##  <a name="addref"></a>  CStringData::AddRef

遞增參考計數的字串物件。

```
void AddRef() throw();
```

### <a name="remarks"></a>備註

遞增參考計數的字串物件。

> [!NOTE]
>  因為負計數會指出字串緩衝區已鎖定，請勿使用負的參考計數，在字串上呼叫這個方法。

##  <a name="data"></a>  CStringData::data

傳回字串物件的字元緩衝區的指標。

```
void* data() throw();
```

### <a name="return-value"></a>傳回值

String 物件的字元緩衝區的指標。

### <a name="remarks"></a>備註

呼叫此函式可傳回目前字元緩衝區的相關聯的字串物件。

> [!NOTE]
>  這個緩衝區未配置之`CStringData`物件但字串管理員時所需。 配置時，緩衝區會附加至字串資料物件。

##  <a name="islocked"></a>  CStringData::IsLocked

決定是否已鎖定的字元緩衝區。

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>傳回值

如果已鎖定的緩衝區，則為 true，則傳回否則為 FALSE。

### <a name="remarks"></a>備註

呼叫此函式來判斷是否字串物件的字元緩衝區目前已鎖定。

##  <a name="isshared"></a>  CStringData::IsShared

決定是否要共用的字元緩衝區。

```
bool IsShared() const throw();
```

### <a name="return-value"></a>傳回值

如果共用緩衝區則為 true，則傳回否則為 FALSE。

### <a name="remarks"></a>備註

呼叫此函式來判斷是否字元緩衝區的字串資料物件目前在多個字串物件之間共用。

##  <a name="lock"></a>  CStringData::Lock

鎖定相關聯的字串物件的字元緩衝區。

```
void Lock() throw();
```

### <a name="remarks"></a>備註

呼叫此函式鎖定字元緩衝區的字串資料物件。 當開發人員需要字元緩衝區的直接存取時，使用鎖定和解除鎖定。 鎖定的理想範例所示[LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)並[UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)方法`CSimpleStringT`。

> [!NOTE]
>  如果在更高版本的字串物件之間共用的緩衝區不只可以鎖定的字元緩衝區。

##  <a name="nalloclength"></a>  CStringData::nAllocLength

已配置的字元緩衝區的長度。

```
int nAllocLength;
```

### <a name="remarks"></a>備註

儲存的配置的資料緩衝區的長度`XCHAR`s （不含終止 null)。

##  <a name="ndatalength"></a>  CStringData::nDataLength

目前 string 物件的長度。

```
int nDataLength;
```

### <a name="remarks"></a>備註

儲存目前使用中的資料長度`XCHAR`s （不含終止 null)。

##  <a name="nrefs"></a>  CStringData::nRefs

字串資料物件的參考計數。

```
long nRefs;
```

### <a name="remarks"></a>備註

儲存字串資料物件的參考計數。 這個計數代表較高層的字串資料物件相關聯的字串物件的數目。 負值表示字串資料物件目前已鎖定。

##  <a name="pstringmgr"></a>  CStringData::pStringMgr

相關聯的 string 物件的記憶體管理員。

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>備註

會儲存相關聯的字串物件的記憶體管理員。 如需有關記憶體管理員和字串的詳細資訊，請參閱[記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

##  <a name="release"></a>  CStringData::Release

遞減參考計數的字串資料物件。

```
void Release() throw();
```

### <a name="remarks"></a>備註

呼叫此函式以遞減參考計數，釋放`CStringData`結構，如果參考計數達到零。 這通常是字串物件遭到刪除，並因此不需要再參考該字串的資料物件時。

例如，下列程式碼會呼叫`CStringData::Release`與字串資料物件相關聯`str1`:

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

##  <a name="unlock"></a>  CStringData::Unlock

解除鎖定相關聯的字串物件的字元緩衝區。

```
void Unlock() throw();
```

### <a name="remarks"></a>備註

呼叫此函式可解除鎖定的字串資料物件的字元緩衝區。 緩衝區未鎖定之後，它是可共用，而且可以參考計數。

> [!NOTE]
>  每次呼叫`Lock`必須符合對應呼叫所`Unlock`。

鎖定和解除鎖定，是開發人員必須確定不共用的字串資料時使用。 鎖定的理想範例所示[LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)並[UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)方法`CSimpleStringT`。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)

