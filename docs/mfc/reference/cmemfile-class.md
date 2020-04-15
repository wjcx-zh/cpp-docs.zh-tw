---
title: CMemFile 類別
ms.date: 11/04/2016
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CMemFile::GrowFile
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
ms.openlocfilehash: 46937795499fd9f697f9778c263a1ee011777c0d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370015"
---
# <a name="cmemfile-class"></a>CMemFile 類別

支援記憶體檔的[CFile](../../mfc/reference/cfile-class.md)派生類。

## <a name="syntax"></a>語法

```
class CMemFile : public CFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMem 檔:CMemFile](#cmemfile)|構造記憶體檔物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMem 檔:附加](#attach)|將記憶體區塊附加到`CMemFile`。|
|[CMemFile::D](#detach)|從分離記憶體塊`CMemFile`並返回指向分離的記憶體塊的指標。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMemFile:Alloc](#alloc)|重寫以修改記憶體分配行為。|
|[CMemFile:免費](#free)|重寫以修改記憶體處理行為。|
|[CMemFile::增長檔](#growfile)|在增長檔時重寫以修改行為。|
|[CMemFile:Memcpy](#memcpy)|在讀取和寫入檔時重寫以修改記憶體複製行為。|
|[CMemFile::真實](#realloc)|重寫以修改記憶體重新分配行為。|

## <a name="remarks"></a>備註

這些記憶體檔與磁碟文件類似,只不過檔案存儲在 RAM 中而不是磁碟上。 記憶體檔案可用於快速暫存記憶體或在獨立進程之間傳輸原始位元組或序列化物件。

`CMemFile`物件可以自動分配自己的記憶體,`CMemFile`也可以通過調用[Attach](#attach)將您自己的記憶體塊附加到物件。 在這兩種情況下,如果`nGrowBytes``nGrowBytes`不是零,則自動以 -大小增量分配用於自動增長記憶體檔的記憶體。

如果記憶體最初由`CMemFile``CMemFile`物件分配,則在破壞物件時將自動刪除記憶體塊;否則,您負責釋放附加到物件的記憶體。

您可以通過調`CMemFile`用[Detach](#detach)將其從物件分離時提供的指標訪問記憶體區塊。

最常見的用途`CMemFile`是創建`CMemFile`物件 ,並通過調用[CFile](../../mfc/reference/cfile-class.md)成員函數使用它。 請注意,創建一`CMemFile`個自動打開它:您不呼用[CFile::open](../../mfc/reference/cfile-class.md#open),僅用於磁碟檔。 由於`CMemFile`不使用磁碟檔案,因此不使用資料成員`CFile::m_hFile`。

`CFile`成員函數[「重複](../../mfc/reference/cfile-class.md#duplicate)」、[鎖定範圍](../../mfc/reference/cfile-class.md#lockrange)和[解鎖範圍](../../mfc/reference/cfile-class.md#unlockrange)未為`CMemFile`實現。 如果在`CMemFile`物件上調用這些函數,您將取得[CNot 支援異常](../../mfc/reference/cnotsupportedexception-class.md)。

`CMemFile`使用運行時庫函數[malloc、realloc](../../c-runtime-library/reference/malloc.md)[和自由分配](../../c-runtime-library/reference/free.md)、重新分配和分配[realloc](../../c-runtime-library/reference/realloc.md)記憶體;和內在[的memcpy,](../../c-runtime-library/reference/memcpy-wmemcpy.md)以阻止複製記憶,當閱讀和寫作。 如果要在增長檔時`CMemFile`更改此行為或行為,請`CMemFile`從相應的函數派生您自己的類並重寫相應的函數。

關於的詳細資訊`CMemFile`,請參閱[MFC](../../mfc/files-in-mfc.md)與[記憶體管理 (MFC)](../../mfc/memory-management.md)中的文章檔,並在*執行時庫參考*中檢視[檔案處理](../../c-runtime-library/file-handling.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="cmemfilealloc"></a><a name="alloc"></a>CMemFile:Alloc

此函數由`CMemFile`成員函數調用。

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>參數

*n 位元組*<br/>
要分配的記憶體位元組數。

### <a name="return-value"></a>傳回值

指向已分配的記憶體區塊的指標;如果分配失敗,則為 NULL。

### <a name="remarks"></a>備註

重寫此函數以實現自定義記憶體分配。 如果重寫此函數,您可能還希望覆蓋[Free](#free)和[Realloc。](#realloc)

默認實現使用運行時庫函數[malloc](../../c-runtime-library/reference/malloc.md)分配記憶體。

## <a name="cmemfileattach"></a><a name="attach"></a>CMem 檔:附加

呼叫此函式以將記憶體區塊附加到`CMemFile`。

```
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>參數

*lpBuffer*<br/>
指向要附加到的緩衝區`CMemFile`的指標。

*n緩衝區大小*<br/>
以位元組為單位指定緩衝區大小的整數。

*n 增長位元組*<br/>
記憶體分配以位元組為單位遞增。

### <a name="remarks"></a>備註

這將導致`CMemFile`使用記憶體塊作為記憶體檔。

如果*nGrowBytes*為`CMemFile`0,則將檔案長度設定為*nBufferSize*。 這意味著記憶體中的數據在附加到之前`CMemFile`將用作檔。 無法以這種方式建立的記憶體檔。

由於無法擴展檔,請注意不要導致`CMemFile`嘗試擴展檔。 例如,`CMemFile`不要調用 CFile 的重寫[:寫入](../../mfc/reference/cfile-class.md#write)結尾寫入,或者不調用[CFile:設置](../../mfc/reference/cfile-class.md#setlength)長度超過*nBufferSize*的長度長度。

如果*nGrowBytes*大於`CMemFile`0, 將忽略已連接的記憶體區塊的內容。 您必須使用`CMemFile`重寫 從頭開始編寫記憶體檔`CFile::Write`的內容 。 如果嘗試寫入檔末尾或透過呼叫`CMemFile``CFile::SetLength`的重寫來成長檔`CMemFile`, 則以*nGrowBytes*的增量增加記憶體配置。 如果傳遞給的記憶體塊`Attach`未使用與[Alloc](#alloc)相容的方法分配,則增長記憶體分配將失敗。 要與 的預設實現相`Alloc`容 ,必須使用執行時庫函數 malloc 或[calloc](../../c-runtime-library/reference/calloc.md)[calloc](../../c-runtime-library/reference/malloc.md)分配記憶體 。

## <a name="cmemfilecmemfile"></a><a name="cmemfile"></a>CMem 檔:CMemFile

第一個重載將打開一個空記憶體檔。

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>參數

*n 增長位元組*<br/>
記憶體分配以位元組為單位遞增。

*lpBuffe*r指標指向一個緩衝區,該緩衝區接收大小*nBufferSize*的資訊。

*n緩衝區大小*<br/>
指定檔緩衝區大小的整數(以位元組為單位)。

### <a name="remarks"></a>備註

請注意,該檔由建構函數打開,並且不應呼叫[CFile:::開啟](../../mfc/reference/cfile-class.md#open)。

第二個重載的作用與使用第一個構造函數並立即調用具有相同參數的[Attach](#attach)相同。 如需詳細資訊，請參閱＜`Attach`＞。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

## <a name="cmemfiledetach"></a><a name="detach"></a>CMemFile::D

調用此函數以獲取指向 正在使用的記憶體區塊`CMemFile`的指標。

```
BYTE* Detach();
```

### <a name="return-value"></a>傳回值

指向包含記憶體檔內容的記憶體區塊的指標。

### <a name="remarks"></a>備註

呼叫此函數也會關閉`CMemFile`。 您可以透過呼叫[Attach](#attach)將`CMemFile`記憶體區重新附加到 。 如果要重新連接檔並使用其中的數據,則應調用[CFile::getLength](../../mfc/reference/cfile-class.md#getlength)以在`Detach`調用 之前獲取檔的長度。 請注意,如果將記憶體區附加到,`CMemFile`以便可以使用其資料 (= `nGrowBytes` 0),則將無法擴展記憶體檔。

## <a name="cmemfilefree"></a><a name="free"></a>CMemFile:免費

此函數由`CMemFile`成員函數調用。

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>參數

*lpMem*<br/>
指標指向要處理的記憶體。

### <a name="remarks"></a>備註

重寫此函數以實現自定義記憶體處理。 如果重寫此函數,您可能還希望重寫[Alloc](#alloc)和[Realloc。](#realloc)

## <a name="cmemfilegrowfile"></a><a name="growfile"></a>CMemFile::增長檔

此函數由多個`CMemFile`成員函數調用。

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>參數

*德紐倫*<br/>
記憶體檔的新大小。

### <a name="remarks"></a>備註

如果要更改其檔的增長方式`CMemFile`,可以重寫它。 預設實現調用[Realloc](#realloc)來擴展現有區塊(或[Alloc](#alloc)以建立記憶體區塊),以建構函數或[Attach](#attach)`nGrowBytes`調用中指定的值的倍數分配記憶體。

## <a name="cmemfilememcpy"></a><a name="memcpy"></a>CMemFile:Memcpy

此函數由`CMemFile` [CFile::讀取](../../mfc/reference/cfile-class.md#read)和[CFile::寫入](../../mfc/reference/cfile-class.md#write)以傳輸數據到記憶體檔並從記憶體檔。

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>參數

*lpMemTarget*<br/>
指向要將源記憶體複製到的記憶體塊的指標。

*lpMem 來源*<br/>
指向源記憶體的指標。

*n 位元組*<br/>
要複製的位元組數目。

### <a name="return-value"></a>傳回值

*lpMemTarget*的副本。

### <a name="remarks"></a>備註

如果要更改執行這些記憶體副本的方式,`CMemFile`則重寫此函數。

## <a name="cmemfilerealloc"></a><a name="realloc"></a>CMemFile::真實

此函數由`CMemFile`成員函數調用。

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>參數

*lpMem*<br/>
指向要重新分配的記憶體塊的指標。

*n 位元組*<br/>
記憶體塊的新大小。

### <a name="return-value"></a>傳回值

如果重新分配失敗,則指向重新分配(並可能移動)的記憶體塊的指標。

### <a name="remarks"></a>備註

重寫此函數以實現自定義記憶體重新分配。 如果重寫此函數,您可能還希望重寫[Alloc](#alloc)和[Free。](#free)

## <a name="see-also"></a>另請參閱

[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
