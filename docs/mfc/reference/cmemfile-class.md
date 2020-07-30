---
title: CMemFile 類別
description: 描述可讓您使用記憶體檔案的 CMemFile 類別中可用的函數。
ms.date: 07/23/2020
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CmemFile::GetBufferPtr
- AFX/CMemFile::GrowFile"
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GetBufferPtr
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
ms.openlocfilehash: edd1d8b8d3979427602bdb61fc7647aec15d58b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222936"
---
# <a name="cmemfile-class"></a>CMemFile 類別

支援記憶體檔案的[CFile](../../mfc/reference/cfile-class.md)衍生類別。

## <a name="syntax"></a>語法

```
class CMemFile : public CFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CMemFile：： CMemFile](#cmemfile)|建立記憶體檔案物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CMemFile：： Attach](#attach)|將記憶體區塊附加至 `CMemFile` 。|
|[CMemFile：:D etach](#detach)|將記憶體區塊從卸離 `CMemFile` ，並將指標傳回至卸離的記憶體區塊。|
|[CMemFile：： GetBufferPtr](#getbufferptr)|取得或寫入記憶體緩衝區，以支援記憶體檔案。|

### <a name="protected-methods"></a>保護方法

|名稱|說明|
|----------|-----------------|
|[CMemFile：：配置](#alloc)|覆寫以修改記憶體配置行為。|
|[CMemFile：： Free](#free)|覆寫以修改記憶體解除配置行為。|
|[CMemFile：： GrowFile](#growfile)|覆寫以修改檔案成長時的行為。|
|[CMemFile：： Memcpy](#memcpy)|覆寫以修改讀取和寫入檔案時的記憶體複製行為。|
|[CMemFile：： Realloc](#realloc)|覆寫以修改記憶體重新配置行為。|

## <a name="remarks"></a>備註

這些記憶體檔案的行為與磁片檔案相似，不同之處在于檔案會儲存在 RAM 中，而不是磁片。 記憶體檔案適用于：

- 快速暫存儲存體
- 在獨立進程之間傳輸原始位元組
- 在獨立進程之間傳輸序列化物件

`CMemFile`物件可以自動設定自己的記憶體。 或者，您可以藉由呼叫 Attach，將您自己的記憶體區塊附加至 `CMemFile` 物件。 [Attach](#attach) 不論是哪一種情況， `nGrowBytes` 如果不是零，就會以大小的增量配置記憶體來成長記憶體檔案 `nGrowBytes` 。

如果物件原本配置記憶體，則記憶體區塊會在物件損毀時自動刪除 `CMemFile` `CMemFile` ; 否則，您必須負責解除配置您附加至物件的記憶體。

藉由呼叫卸離，您可以透過從物件卸離時所提供的指標來存取記憶體區塊 `CMemFile` 。 [Detach](#detach)

最常見的用法 `CMemFile` 是建立 `CMemFile` 物件，並藉由呼叫[CFile](../../mfc/reference/cfile-class.md)成員函式來使用它。 建立 `CMemFile` 會自動開啟它：您不會呼叫[CFile：： Open](../../mfc/reference/cfile-class.md#open)，這只會用於磁片檔案。 因為 `CMemFile` 不會使用磁片檔案，所以不會 `CFile::m_hFile` 使用資料成員。

`CFile`不會為[Duplicate](../../mfc/reference/cfile-class.md#duplicate) [LockRange](../../mfc/reference/cfile-class.md#lockrange)和[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)成員函式 `CMemFile` 。 如果您在物件上呼叫這些函式 `CMemFile` ，將會取得[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

`CMemFile`會使用執行時間程式庫函式[malloc](../../c-runtime-library/reference/malloc.md)、 [realloc](../../c-runtime-library/reference/realloc.md)和[free](../../c-runtime-library/reference/free.md)來配置、重新分配和解除配置記憶體;和內建[memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)會在讀取和寫入時封鎖複製記憶體。 如果您想要變更此行為或成長檔案時的行為 `CMemFile` ，請從衍生您自己的類別， `CMemFile` 並覆寫適當的函式。

如需有關的詳細資訊 `CMemFile` ，請參閱 MFC 和[記憶體管理（mfc）](../../mfc/memory-management.md) [中的檔](../../mfc/files-in-mfc.md)，並參閱《*執行時間程式庫參考*》中的檔案[處理](../../c-runtime-library/file-handling.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>需求

**標頭：** afx。h

## <a name="cmemfilealloc"></a><a name="alloc"></a>CMemFile：：配置

此函式是由成員函式所呼叫 `CMemFile` 。

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>參數

*nBytes*<br/>
要配置的記憶體位元組數。

### <a name="return-value"></a>傳回值

已配置之記憶體區塊的指標，如果配置失敗，則為 Null。

### <a name="remarks"></a>備註

覆寫此函式以執行自訂記憶體配置。 如果您覆寫此函式，您可能也會想要覆寫[Free](#free)和[Realloc](#realloc) 。

預設的執行會使用執行時間程式庫函數[malloc](../../c-runtime-library/reference/malloc.md)來配置記憶體。

## <a name="cmemfileattach"></a><a name="attach"></a>CMemFile：： Attach

呼叫此函式可將記憶體區塊附加至 `CMemFile` 。

```cpp
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>參數

*lpBuffer*<br/>
要附加至之緩衝區的指標 `CMemFile` 。

*nBufferSize*<br/>
指定緩衝區大小（以位元組為單位）的整數。

*nGrowBytes*<br/>
記憶體配置增量（以位元組為單位）。

### <a name="remarks"></a>備註

這會導致 `CMemFile` 使用記憶體區塊做為記憶體檔案。

如果*nGrowBytes*為0， `CMemFile` 會將檔案長度設定為*nBufferSize*。 這表示在連接之前，記憶體區塊中的資料 `CMemFile` 將會用來做為檔案。 以這種方式建立的記憶體檔案無法成長。

因為檔案無法成長，請小心不要造成 `CMemFile` 嘗試擴大檔案。 例如，請勿呼叫 `CMemFile` [CFile： write](../../mfc/reference/cfile-class.md#write)的覆寫結束，或不要呼叫長度超過*NBufferSize*的[CFile： SetLength](../../mfc/reference/cfile-class.md#setlength) 。

如果*nGrowBytes*大於0， `CMemFile` 將會忽略您附加的記憶體區塊內容。 您必須使用的覆寫從頭開始寫入記憶體檔案的內容 `CMemFile` `CFile::Write` 。 如果您嘗試寫入超過檔案結尾，或藉由呼叫的覆寫來增加檔案 `CMemFile` `CFile::SetLength` ， `CMemFile` 將會以*nGrowBytes*的增量來增加記憶體配置。 如果您傳遞給的記憶體區塊未配置給與「配置」 `Attach` 相容的方法，則記憶體[Alloc](#alloc)配置的成長將會失敗。 若要與的預設執行相容 `Alloc` ，您必須使用執行時間程式庫函數[malloc](../../c-runtime-library/reference/malloc.md)或[calloc](../../c-runtime-library/reference/calloc.md)來配置記憶體。

## <a name="cmemfilecmemfile"></a><a name="cmemfile"></a>CMemFile：： CMemFile

第一個多載會開啟空的記憶體檔案。

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>參數

*nGrowBytes*<br/>
記憶體配置增量（以位元組為單位）。

*lpBuffer*緩衝區的指標，接收大小*nBufferSize*的資訊。

*nBufferSize*<br/>
指定檔案緩衝區大小的整數（以位元組為單位）。

### <a name="remarks"></a>備註

檔案是由「函式」開啟。 不要呼叫[CFile：： Open](../../mfc/reference/cfile-class.md#open)。

第二個多載的作用等同于您使用第一個函式，並立即以相同的參數呼叫[Attach](#attach) 。 如需詳細資訊，請參閱＜`Attach`＞。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

## <a name="cmemfiledetach"></a><a name="detach"></a>CMemFile：:D etach

呼叫此函式可取得所使用之記憶體區塊的指標 `CMemFile` 。

```
BYTE* Detach();
```

### <a name="return-value"></a>傳回值

記憶體區塊的指標，其中包含記憶體檔案的內容。

### <a name="remarks"></a>備註

呼叫此函式也會關閉 `CMemFile` 。 您可以藉 `CMemFile` 由呼叫[Attach](#attach)，將記憶體區塊重新附加至。 如果您想要重新附加檔案並使用其中的資料，您應該先呼叫[CFile：： GetLength](../../mfc/reference/cfile-class.md#getlength)來取得檔案的長度，然後再呼叫 `Detach` 。 如果您將記憶體區塊附加到， `CMemFile` 讓您可以使用其資料（ `nGrowBytes` = = 0），則無法增加記憶體檔案。

## <a name="cmemfilefree"></a><a name="free"></a>CMemFile：： Free

此函式是由成員函式所呼叫 `CMemFile` 。

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>參數

*lpMem*<br/>
要解除配置之記憶體的指標。

### <a name="remarks"></a>備註

覆寫此函式以執行自訂記憶體解除配置。 如果您[覆寫此](#alloc)函式，您可能也會想要覆寫配置和[Realloc](#realloc) 。

## <a name="cmemfilegetbufferptr"></a><a name="getbufferptr"></a>CMemFile：： GetBufferPtr

取得或寫入記憶體緩衝區，以支援記憶體檔案。

```cpp
virtual UINT GetBufferPtr(
    UINT nCommand,
    UINT nCount = 0,
    void** ppBufStart = NULL,
    void** ppBufMax = NULL
);
```

### <a name="parameters"></a>參數

*nCommand*<br/>
要執行的[bufferCommand](buffercommand-enumeration.md) （ `bufferCheck` 、 `bufferCommit` 、 `bufferRead` 或 `bufferWrite` ）。

*nCount*<br/>
視*nCommand*而定，緩衝區中要讀取、寫入或認可的位元組數目。 從緩衝區讀取時，請指定-1，以傳回從目前位置到檔案結尾的緩衝區。

*ppBufStart*<br/>
脫銷緩衝區的開頭。 `NULL`當*nCommand*為時，必須是 `bufferCommit` 。

*ppBufMax*<br/>
脫銷緩衝區的結尾。 `NULL`當 nCommand 為時，必須是 `bufferCommit` 。

### <a name="return-value"></a>傳回值

| *命令*值 | 傳回值 |
|--|--|
| `buffercheck` | 如果支援直接緩衝，則會傳回[bufferDirect](buffercommand-enumeration.md) ，否則會傳回0。 |
| `bufferCommit` | 傳回 `0`。 |
| `bufferRead` 或 `bufferWrite` | 傳回傳回的緩衝區空間中的位元組數目。 *ppBufStart*和*ppBufMax*指向讀取/寫入緩衝區的開頭和結尾。  |

### <a name="remarks"></a>備註

記憶體緩衝區中的目前位置（ `m_nPosition` ）會以下列方式進行，視*nCommand*而定：

| *nCommand* | 緩衝區位置 |
|-|-|
| `bufferCommit` | 目前的位置會向前推進認可的緩衝區大小。 |
| `bufferRead` | 目前的位置會前進到讀取緩衝區的大小。 |

## <a name="cmemfilegrowfile"></a><a name="growfile"></a>CMemFile：： GrowFile

此函式是由數個成員函式所呼叫 `CMemFile` 。

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>參數

*dwNewLen*<br/>
記憶體檔案的新大小。

### <a name="remarks"></a>備註

如果您想要變更其檔案的成長方式，可以覆寫它 `CMemFile` 。 預設的執行會呼叫[Realloc](#realloc)來成長現有的區塊（[或配置](#alloc)以建立記憶體區塊），並以在此函式 `nGrowBytes` 中指定之值的倍數或[附加](#attach)呼叫來配置記憶體。

## <a name="cmemfilememcpy"></a><a name="memcpy"></a>CMemFile：： Memcpy

`CMemFile` [CFile：： Read](../../mfc/reference/cfile-class.md#read)和[CFile：： Write](../../mfc/reference/cfile-class.md#write)的覆寫會呼叫這個函式，以將資料傳入和傳出記憶體檔案。

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>參數

*lpMemTarget*<br/>
將複製來源記憶體的記憶體區塊指標。

*lpMemSource*<br/>
來源記憶體區塊的指標。

*nBytes*<br/>
要複製的位元組數目。

### <a name="return-value"></a>傳回值

*LpMemTarget*的複本。

### <a name="remarks"></a>備註

如果您想要變更 `CMemFile` 執行這些記憶體複製的方式，請覆寫此函式。

## <a name="cmemfilerealloc"></a><a name="realloc"></a>CMemFile：： Realloc

此函式是由成員函式所呼叫 `CMemFile` 。

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>參數

*lpMem*<br/>
要重新配置之記憶體區塊的指標。

*nBytes*<br/>
記憶體區塊的新大小。

### <a name="return-value"></a>傳回值

已重新配置（而且可能已移動）之記憶體區塊的指標，如果重新配置失敗，則為 Null。

### <a name="remarks"></a>備註

覆寫此函式以執行自訂記憶體重新配置。 如果您[覆寫此](#alloc)函式，您可能也會想要覆寫配置和[免費](#free)。

## <a name="see-also"></a>另請參閱

[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
