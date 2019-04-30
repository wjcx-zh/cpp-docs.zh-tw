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
ms.openlocfilehash: a57f4e245ca1e93ec0edd454a7f407aeda5beca4
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341680"
---
# <a name="cmemfile-class"></a>CMemFile 類別

[CFile](../../mfc/reference/cfile-class.md)-衍生類別，可支援記憶體檔案。

## <a name="syntax"></a>語法

```
class CMemFile : public CFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMemFile::CMemFile](#cmemfile)|建構記憶體檔案物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMemFile::Attach](#attach)|將附加到的記憶體區塊`CMemFile`。|
|[CMemFile::Detach](#detach)|中斷連結中的記憶體區塊`CMemFile`和讓指標回到卸離的記憶體區塊。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMemFile::Alloc](#alloc)|若要修改的記憶體配置行為來覆寫。|
|[CMemFile::Free](#free)|覆寫以修改記憶體解除配置行為。|
|[CMemFile::GrowFile](#growfile)|覆寫以修改增大檔案時的行為。|
|[CMemFile::Memcpy](#memcpy)|覆寫以修改讀取和寫入檔案時，記憶體複製行為。|
|[CMemFile::Realloc](#realloc)|覆寫以修改記憶體重新配置行為。|

## <a name="remarks"></a>備註

這些記憶體檔案的行為如同磁碟檔案之處在於此檔案會儲存在 RAM 中，而不是在磁碟上。 記憶體檔案適合用於快速暫時儲存或傳輸未經處理位元組或序列化的獨立處理序之間的物件。

`CMemFile` 物件可以自動配置自己的記憶體，或者您可以附加至您自己的記憶體區塊`CMemFile`藉由呼叫物件[附加](#attach)。 在任一情況下，在配置為自動成長的記憶體檔案的記憶體`nGrowBytes`-如果大小遞增`nGrowBytes`不是零。

記憶體區塊會自動刪除時的解構`CMemFile`物件記憶體的原始配置的`CMemFile`物件; 否則您必須負責解除配置您附加至物件的記憶體。

您可以透過從您中斷連結時所提供的指標來存取的記憶體區塊`CMemFile`藉由呼叫物件[卸離](#detach)。

最常見的用法`CMemFile`是建立`CMemFile`物件，並使用藉由呼叫[CFile](../../mfc/reference/cfile-class.md)成員函式。 請注意，建立`CMemFile`會自動開啟它： 您不能呼叫[CFile::Open](../../mfc/reference/cfile-class.md#open)，它只用於磁碟檔案。 因為`CMemFile`不會使用磁碟檔案的資料成員`CFile::m_hFile`未使用。

`CFile`成員函式[重複](../../mfc/reference/cfile-class.md#duplicate)， [LockRange](../../mfc/reference/cfile-class.md#lockrange)，和[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)並未實作`CMemFile`。 如果您在上呼叫這些函式`CMemFile`物件，您會收到[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

`CMemFile` 使用執行階段程式庫函式[malloc](../../c-runtime-library/reference/malloc.md)， [realloc](../../c-runtime-library/reference/realloc.md)，並[免費](../../c-runtime-library/reference/free.md)配置，重新配置和解除配置記憶體，並內建[memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)區塊複製記憶體讀取和寫入時。 如果您想要變更此行為時`CMemFile`成長的檔案中，衍生您自己的類別，從`CMemFile`並覆寫適當的函式。

如需詳細資訊`CMemFile`，請參閱文章[MFC 中的檔案](../../mfc/files-in-mfc.md)並[記憶體管理 (MFC)](../../mfc/memory-management.md)看[檔案處理](../../c-runtime-library/file-handling.md)中*執行階段程式庫參考*。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CMemFile`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="alloc"></a>  CMemFile::Alloc

此函式會呼叫`CMemFile`成員函式。

```
virtual BYTE* Alloc(SIZE_T nBytes);
```

### <a name="parameters"></a>參數

*nBytes*<br/>
要配置的記憶體位元組數目。

### <a name="return-value"></a>傳回值

已配置的記憶體區塊的指標或 NULL 若配置失敗。

### <a name="remarks"></a>備註

覆寫這個函式，以實作自訂的記憶體配置。 如果您覆寫這個函式，您可能會想要覆寫[空閒](#free)並[Realloc](#realloc)以及。

預設實作會使用執行階段程式庫函式[malloc](../../c-runtime-library/reference/malloc.md)配置記憶體。

##  <a name="attach"></a>  CMemFile::Attach

呼叫此函式來附加到的記憶體區塊`CMemFile`。

```
void Attach(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>參數

*lpBuffer*<br/>
要附加至緩衝區的指標`CMemFile`。

*nBufferSize*<br/>
整數，指定緩衝區的大小，以位元組為單位。

*nGrowBytes*<br/>
以位元組為單位的記憶體配置遞增值。

### <a name="remarks"></a>備註

這會導致`CMemFile`為記憶體檔案中使用的記憶體區塊。

如果*nGrowBytes*為 0，`CMemFile`將會設定為檔案的長度*nBufferSize*。 這表示記憶體區塊中的資料之前它已附加至`CMemFile`將用於做為檔案。 以這種方式建立記憶體檔案無法成長。

由於檔案無法為而成長，請小心不要造成`CMemFile`嘗試將檔案成長。 比方說，不要呼叫`CMemFile`的覆寫[CFile:Write](../../mfc/reference/cfile-class.md#write)來撰寫結尾，或不要呼叫[CFile:SetLength](../../mfc/reference/cfile-class.md#setlength)長度超過*nBufferSize*。

如果*nGrowBytes*大於 0，`CMemFile`會忽略連結之後的記憶體區塊的內容。 您必須從臨時使用寫入記憶體檔案的內容`CMemFile`覆寫`CFile::Write`。 如果您嘗試寫入超過檔案結尾或成長的檔案，藉由呼叫`CMemFile`覆寫`CFile::SetLength`，`CMemFile`將會成長的遞增量的記憶體配置*nGrowBytes*。 如果您傳遞給記憶體區塊成長的記憶體配置將會失敗`Attach`相容的方法未配置[配置](#alloc)。 預設實作相容`Alloc`，您必須配置的記憶體與執行階段程式庫函式[malloc](../../c-runtime-library/reference/malloc.md)或是[calloc](../../c-runtime-library/reference/calloc.md)。

##  <a name="cmemfile"></a>  CMemFile::CMemFile

第一個多載會開啟空白記憶體檔案。

```
CMemFile(UINT nGrowBytes = 1024);

CMemFile(
    BYTE* lpBuffer,
    UINT nBufferSize,
    UINT nGrowBytes = 0);
```

### <a name="parameters"></a>參數

*nGrowBytes*<br/>
以位元組為單位的記憶體配置遞增值。

*lpBuffe*r 指標，接收到的資訊大小的緩衝區*nBufferSize*。

*nBufferSize*<br/>
整數，指定檔案緩衝區大小，以位元組為單位。

### <a name="remarks"></a>備註

請注意，建構函式開啟的檔案，而且，您不應該呼叫[CFile::Open](../../mfc/reference/cfile-class.md#open)。

第二個多載作用相同，因為，如果您使用第一個建構函式，並立即呼叫[附加](#attach)使用相同的參數。 如需詳細資訊，請參閱`Attach`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]

##  <a name="detach"></a>  CMemFile::Detach

呼叫此函式，以取得正在使用的記憶體區塊的指標`CMemFile`。

```
BYTE* Detach();
```

### <a name="return-value"></a>傳回值

包含記憶體檔案的內容的記憶體區塊指標。

### <a name="remarks"></a>備註

呼叫此函式也會關閉`CMemFile`。 您可以重新連接到的記憶體區塊`CMemFile`藉由呼叫[附加](#attach)。 如果您想要重新附加檔案，並在其中使用的資料，您應該呼叫[CFile::GetLength](../../mfc/reference/cfile-class.md#getlength)要取得其長度的檔案，然後再呼叫`Detach`。 請注意，如果您將附加到的記憶體區塊`CMemFile`，讓您可以使用它的資料 ( `nGrowBytes` = = 0)，則您將無法檔案成長的記憶體。

##  <a name="free"></a>  CMemFile::Free

此函式會呼叫`CMemFile`成員函式。

```
virtual void Free(BYTE* lpMem);
```

### <a name="parameters"></a>參數

*lpMem*<br/>
要解除配置的記憶體指標。

### <a name="remarks"></a>備註

覆寫這個函式，以實作自訂記憶體解除配置。 如果您覆寫這個函式，您可能會想要覆寫[Alloc](#alloc)並[Realloc](#realloc)以及。

##  <a name="growfile"></a>  CMemFile::GrowFile

此函式會呼叫數個`CMemFile`成員函式。

```
virtual void GrowFile(SIZE_T dwNewLen);
```

### <a name="parameters"></a>參數

*dwNewLen*<br/>
新的記憶體檔案的大小。

### <a name="remarks"></a>備註

您可以覆寫它如果您想要變更如何`CMemFile`其檔案的成長。 預設實作會呼叫[Realloc](#realloc)成長現有區塊 (或[Alloc](#alloc)若要建立的記憶體區塊)，配置記憶體以 64kb 的倍數`nGrowBytes`建構函式中指定的值或[附加](#attach)呼叫。

##  <a name="memcpy"></a>  CMemFile::Memcpy

會呼叫此函式`CMemFile`的覆寫[CFile::Read](../../mfc/reference/cfile-class.md#read)並[CFile::Write](../../mfc/reference/cfile-class.md#write)傳輸進出記憶體檔案的資料。

```
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,
    const BYTE* lpMemSource,
    SIZE_T nBytes);
```

### <a name="parameters"></a>參數

*lpMemTarget*<br/>
將複製的來源記憶體的記憶體區塊的指標。

*lpMemSource*<br/>
來源的記憶體區塊指標。

*nBytes*<br/>
要複製的位元組數目。

### <a name="return-value"></a>傳回值

一份*lpMemTarget*。

### <a name="remarks"></a>備註

覆寫這個函式，如果您想要變更的方式，`CMemFile`沒有這些記憶體複本。

##  <a name="realloc"></a>  CMemFile::Realloc

此函式會呼叫`CMemFile`成員函式。

```
virtual BYTE* Realloc(
    BYTE* lpMem,
    SIZE_T nBytes);
```

### <a name="parameters"></a>參數

*lpMem*<br/>
重新配置的記憶體區塊指標。

*nBytes*<br/>
新的記憶體區塊的大小。

### <a name="return-value"></a>傳回值

已重新配置 （和可能的移動） 記憶體區塊的指標或如果重新配置失敗，則為 NULL。

### <a name="remarks"></a>備註

覆寫這個函式，以實作自訂記憶體重新配置。 如果您覆寫這個函式，您可能會想要覆寫[Alloc](#alloc)並[免費](#free)以及。

## <a name="see-also"></a>另請參閱

[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
