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
ms.openlocfilehash: 140836f45ed2f4088bc0baed67676f93cb268d01
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832109"
---
# <a name="cstringdata-class"></a>CStringData 類別

此類別代表字串物件的資料。

## <a name="syntax"></a>語法

```
struct CStringData
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|名稱|描述|
|-|-|
|[AddRef](#addref)|遞增字串資料物件的參考計數。|
|[data](#data)|捕獲字串物件的字元資料。|
|[IsLocked](#islocked)|判斷相關聯之字串物件的緩衝區是否已鎖定。|
|[IsShared](#isshared)|判斷相關聯之字串物件的緩衝區目前是否為共用。|
|[鎖定](#lock)|鎖定相關聯之字串物件的緩衝區。|
|[版本](#release)|釋放指定的字串物件。|
|[解 鎖](#unlock)|解除鎖定相關聯之字串物件的緩衝區。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|-|-|
|[nAllocLength](#nalloclength)|中配置資料的長度 `XCHAR` (不包括終止的 null) |
|[nDataLength](#ndatalength)|中目前使用的資料長度 `XCHAR` (不包括終止的 null) |
|[nRefs](#nrefs)|物件的目前參考計數。|
|[pStringMgr](#pstringmgr)|此字串物件的字串管理員指標。|

## <a name="remarks"></a>備註

此類別只應由執行自訂字串管理員的開發人員使用。 如需自訂字串管理員的詳細資訊，請參閱 [記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)

這個類別會封裝不同類型的資訊，以及與較高字串物件相關聯的資料，例如 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)、 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)或 [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) 物件。 每個較高的字串物件都包含其相關聯物件的指標 `CStringData` ，讓多個字串物件指向相同的字串資料物件。 此關聯性是以物件的參考計數 () 來表示 `nRefs` `CStringData` 。

> [!NOTE]
> 在某些情況下，字串類型 (例如 `CFixedString`) 不會與一個以上的字串物件共用字串資料物件。 如需有關這個的詳細資訊，請參閱 [記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

這項資料是由下列各項所組成：

- 記憶體管理員 (字串的類型 [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) 。

- 目前的長度 ( [nDataLength](#ndatalength) 字串) 。

- 配置的長度 ( [nAllocLength](#nalloclength) 字串) 。 基於效能考慮，這可能不同于目前的字串長度

- 目前的參考計數 ( [nRefs](#nrefs) 物件的) `CStringData` 。 這個值是用來判斷有多少個字串物件共用相同的 `CStringData` 物件。

- 實際的字元緩衝區 ( 字串的 [資料](#data)) 。

   > [!NOTE]
   > 字串物件的實際字元緩衝區是由字串管理員所配置，並附加至 `CStringData` 物件。

## <a name="requirements"></a>規格需求

**標頭：** atlsimpstr。h

## <a name="cstringdataaddref"></a><a name="addref"></a> CStringData：： AddRef

遞增字串物件的參考計數。

```cpp
void AddRef() throw();
```

### <a name="remarks"></a>備註

遞增字串物件的參考計數。

> [!NOTE]
> 請勿在具有負參考計數的字串上呼叫這個方法，因為負計數表示已鎖定字串緩衝區。

## <a name="cstringdatadata"></a><a name="data"></a> CStringData：:d ata

傳回字串物件之字元緩衝區的指標。

```cpp
void* data() throw();
```

### <a name="return-value"></a>傳回值

字串物件之字元緩衝區的指標。

### <a name="remarks"></a>備註

呼叫此函式可傳回相關聯之字串物件的目前字元緩衝區。

> [!NOTE]
> 這個緩衝區不是由物件配置， `CStringData` 而是由字串管理員在需要時配置。 當配置時，緩衝區會附加至字串資料物件。

## <a name="cstringdataislocked"></a><a name="islocked"></a> CStringData：： IsLocked

判斷是否鎖定字元緩衝區。

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>傳回值

如果緩衝區已鎖定，則傳回 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

呼叫此函式，以判斷字串物件的字元緩衝區目前是否已鎖定。

## <a name="cstringdataisshared"></a><a name="isshared"></a> CStringData：： IsShared

判斷是否共用字元緩衝區。

```
bool IsShared() const throw();
```

### <a name="return-value"></a>傳回值

如果緩衝區是共用的，則傳回 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

呼叫此函式，以判斷字串資料物件的字元緩衝區目前是否在多個字串物件之間共用。

## <a name="cstringdatalock"></a><a name="lock"></a> CStringData：： Lock

鎖定相關聯之字串物件的字元緩衝區。

```cpp
void Lock() throw();
```

### <a name="remarks"></a>備註

呼叫此函式可鎖定字串資料物件的字元緩衝區。 當開發人員需要直接存取字元緩衝區時，就會使用鎖定和解除鎖定。 的 [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) 和 [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) 方法示範了一個很好的鎖定範例 `CSimpleStringT` 。

> [!NOTE]
> 只有在較高的字串物件之間不共用緩衝區時，才能鎖定字元緩衝區。

## <a name="cstringdatanalloclength"></a><a name="nalloclength"></a> CStringData：： nAllocLength

配置之字元緩衝區的長度。

```
int nAllocLength;
```

### <a name="remarks"></a>備註

將配置的資料緩衝區長度儲存在 s 中， `XCHAR` (不包括終止的 null) 。

## <a name="cstringdatandatalength"></a><a name="ndatalength"></a> CStringData：： nDataLength

字串物件的目前長度。

```
int nDataLength;
```

### <a name="remarks"></a>備註

將目前使用中資料的長度儲存在 `XCHAR` s (不包括終止的 null) 。

## <a name="cstringdatanrefs"></a><a name="nrefs"></a> CStringData：： nRefs

字串資料物件的參考計數。

```
long nRefs;
```

### <a name="remarks"></a>備註

儲存字串資料物件的參考計數。 此計數表示與字串資料物件相關聯的字串物件數目上限。 負數值表示字串資料物件目前已鎖定。

## <a name="cstringdatapstringmgr"></a><a name="pstringmgr"></a> CStringData：:p StringMgr

相關聯之字串物件的記憶體管理員。

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>備註

儲存相關聯之字串物件的記憶體管理員。 如需記憶體管理員和字串的詳細資訊，請參閱 [記憶體管理和 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)。

## <a name="cstringdatarelease"></a><a name="release"></a> CStringData：： Release

遞減字串資料物件的參考計數。

```cpp
void Release() throw();
```

### <a name="remarks"></a>備註

呼叫此函式可遞減參考計數，並在 `CStringData` 參考計數到達零時釋放結構。 這通常是在刪除字串物件時完成，因此不再需要參考字串資料物件。

例如，下列程式碼會呼叫 `CStringData::Release` 與相關聯的字串資料物件 `str1` ：

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

## <a name="cstringdataunlock"></a><a name="unlock"></a> CStringData：： Unlock

解除鎖定相關聯之字串物件的字元緩衝區。

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>備註

呼叫此函式可解除鎖定字串資料物件的字元緩衝區。 一旦緩衝區解除鎖定，就可以共用，而且可以參考計數。

> [!NOTE]
> 的每個呼叫都 `Lock` 必須透過對應的呼叫來進行比對 `Unlock` 。

當開發人員必須確保不共用字串資料時，就會使用鎖定和解除鎖定。 的 [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) 和 [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) 方法示範了一個很好的鎖定範例 `CSimpleStringT` 。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共用類別](../../atl-mfc-shared/atl-mfc-shared-classes.md)
