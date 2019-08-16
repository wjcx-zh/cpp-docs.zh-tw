---
title: CSharedFile 類別
ms.date: 11/04/2016
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
ms.openlocfilehash: 74a34ec169868d3e28f78f33da38dbda21ef23b3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502605"
---
# <a name="csharedfile-class"></a>CSharedFile 類別

支援共用記憶體檔案的[CMemFile](../../mfc/reference/cmemfile-class.md)衍生類別。

## <a name="syntax"></a>語法

```
class CSharedFile : public CMemFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSharedFile::CSharedFile](#csharedfile)|建構 `CSharedFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSharedFile::Detach](#detach)|關閉共用記憶體檔案, 並傳回其記憶體區塊的控制碼。|
|[CSharedFile::SetHandle](#sethandle)|將共用記憶體檔案附加至記憶體區塊。|

## <a name="remarks"></a>備註

記憶體檔案的行為與磁片檔案相同。 差別在於, 記憶體檔案會儲存在 RAM 中, 而不是存放在磁片上。 記憶體檔案適用于快速暫存儲存, 或在獨立進程之間傳送未經處理的位元組或序列化物件。

共用記憶體檔案與其他記憶體檔案不同的是, 記憶體中的檔案是使用[GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows 函式配置的。 類別會將資料儲存在全域配置的記憶體區塊中 ( `GlobalAlloc`使用建立), 而這個記憶體區塊可以使用 DDE、剪貼簿或其他 OLE/COM 制式資料傳輸作業來共用, 例如使用`IDataObject`。 `CSharedFile`

`GlobalAlloc`傳回 HGLOBAL 控制碼, 而不是記憶體的指標, 例如[malloc](../../c-runtime-library/reference/malloc.md)傳回的指標。 某些應用程式中需要 HGLOBAL 控制碼。 例如, 若要將資料放在剪貼簿上, 您需要 HGLOBAL 控制碼。

`CSharedFile`不會使用記憶體對應檔案, 而且不能直接在進程之間共用資料。

`CSharedFile`物件可以自動設定自己的記憶體。 或者, 您可以藉由呼叫`CSharedFile` [CSharedFile:: SetHandle](#sethandle), 將自己的記憶體區塊附加至物件。 不論是哪一種情況, 如果`nGrowBytes` `nGrowBytes`不是零, 就會以大小的增量配置記憶體來成長記憶體檔案。

如需詳細資訊, 請參閱《*執行時間程式庫參考*》中的在 MFC 和檔案[處理](../../c-runtime-library/file-handling.md)中的[檔](../../mfc/files-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>需求

**標頭:** afxadv。h

##  <a name="csharedfile"></a>CSharedFile::CSharedFile

建立`CSharedFile`物件並為其配置記憶體。

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>參數

*nAllocFlags*<br/>
表示如何配置記憶體的旗標。 如需有效旗標值的清單, 請參閱[GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) 。

*nGrowBytes*<br/>
記憶體配置增量 (以位元組為單位)。

##  <a name="detach"></a>CSharedFile::D etach

呼叫此函式以關閉記憶體檔案, 並將它與記憶體區塊卸離。

```
HGLOBAL Detach();
```

### <a name="return-value"></a>傳回值

記憶體區塊的控制碼, 其中包含記憶體檔案的內容。

### <a name="remarks"></a>備註

您可以使用卸**離**所傳回的控制碼, 藉由呼叫[SetHandle](#sethandle)來重新開啟它。

##  <a name="sethandle"></a>CSharedFile::SetHandle

呼叫此函式可將全域記憶體區塊附加至`CSharedFile`物件。

```
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>參數

*hGlobalMemory*<br/>
要附加至`CSharedFile`的全域記憶體的控制碼。

*bAllowGrow*<br/>
指定是否允許記憶體區塊成長。

### <a name="remarks"></a>備註

如果*bAllowGrow*為非零值, 則記憶體區塊的大小會視需要而增加, 例如, 如果您嘗試將比記憶體區塊大小還要多的位元組寫入檔案。

## <a name="see-also"></a>另請參閱

[CMemFile 類別](../../mfc/reference/cmemfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMemFile 類別](../../mfc/reference/cmemfile-class.md)
