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
ms.openlocfilehash: 0a9bbf3072a665c04501025d421839fa90a37225
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344413"
---
# <a name="csharedfile-class"></a>CSharedFile 類別

[CMemFile](../../mfc/reference/cmemfile-class.md)-衍生的類別支援共用記憶體檔案。

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
|[CSharedFile::Detach](#detach)|關閉共用的記憶體檔案，並傳回其記憶體區塊的控制代碼。|
|[CSharedFile::SetHandle](#sethandle)|附加的共用的記憶體檔案的記憶體區塊。|

## <a name="remarks"></a>備註

記憶體檔案的行為類似磁碟檔案。 差別在於，記憶體檔案會儲存在 RAM 中，而不是在磁碟上。 記憶體檔案是用來快速暫存儲存體，或傳送未經處理位元組或序列化的獨立處理序之間的物件。

與其他記憶體檔案，因為它們的記憶體配置使用不同的共用的記憶體檔案[GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) Windows 函式。 `CSharedFile`類別會將資料儲存在全域配置的記憶體區塊 (使用建立`GlobalAlloc`)，而此記憶體區塊可以共用使用 DDE、 剪貼簿或其他 OLE/COM 制式資料傳輸作業，例如，使用`IDataObject`。

`GlobalAlloc` 傳回 HGLOBAL 處理而不是記憶體中，例如傳回指標的指標[malloc](../../c-runtime-library/reference/malloc.md)。 某些應用程式中需要 HGLOBAL 控制代碼。 比方說，若要將資料放在剪貼簿上您會需要 HGLOBAL 控制代碼。

`CSharedFile` 不使用記憶體對應檔案和資料不會直接處理序之間共用。

`CSharedFile` 物件可以自動配置自己的記憶體。 或者，您可以將您自己的記憶體區塊，來附加`CSharedFile`藉由呼叫物件[CSharedFile::SetHandle](#sethandle)。 在任一情況下，在配置為自動成長的記憶體檔案的記憶體`nGrowBytes`-如果大小遞增`nGrowBytes`不是零。

如需詳細資訊，請參閱文章[MFC 中的檔案](../../mfc/files-in-mfc.md)並[檔案處理](../../c-runtime-library/file-handling.md)中*執行階段程式庫參考*。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>需求

**標頭：** afxadv.h

##  <a name="csharedfile"></a>  CSharedFile::CSharedFile

建構`CSharedFile`物件，並會配置的記憶體。

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>參數

*nAllocFlags*<br/>
指出記憶體的配置方式的旗標。 請參閱[GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc)取得一份有效的旗標值。

*nGrowBytes*<br/>
以位元組為單位的記憶體配置遞增值。

##  <a name="detach"></a>  CSharedFile::Detach

呼叫此函式來關閉記憶體檔案，並中斷的記憶體區塊。

```
HGLOBAL Detach();
```

### <a name="return-value"></a>傳回值

包含記憶體檔案的內容的記憶體區塊的控制代碼。

### <a name="remarks"></a>備註

您可以藉由呼叫重新開啟它[sethandle，然後](#sethandle)，使用傳回的控制代碼**卸離**。

##  <a name="sethandle"></a>  CSharedFile::SetHandle

呼叫此函式來附加至全域記憶體區塊`CSharedFile`物件。

```
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>參數

*hGlobalMemory*<br/>
要附加至的全域記憶體控制代碼`CSharedFile`。

*bAllowGrow*<br/>
指定是否允許之記憶體區塊成長。

### <a name="remarks"></a>備註

如果*bAllowGrow*為非零值，記憶體區塊的大小會增加如有必要，比方說，如果您嘗試寫入記憶體區塊的大小比檔案中的位元組數目。

## <a name="see-also"></a>另請參閱

[CMemFile 類別](../../mfc/reference/cmemfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMemFile 類別](../../mfc/reference/cmemfile-class.md)
