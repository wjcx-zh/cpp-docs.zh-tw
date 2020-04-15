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
ms.openlocfilehash: e6a713ac9d9e906ec204d4a52b43ed51c08fd99c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318423"
---
# <a name="csharedfile-class"></a>CSharedFile 類別

支援共用記憶體檔的[CMemFile](../../mfc/reference/cmemfile-class.md)派生類。

## <a name="syntax"></a>語法

```
class CSharedFile : public CMemFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 分享檔案:C 分享檔案](#csharedfile)|建構 `CSharedFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[共用檔案::D](#detach)|關閉共用記憶體檔並返回其記憶體區塊的句柄。|
|[C 分享檔案::設定句柄](#sethandle)|將共用記憶體檔附加到記憶體區塊。|

## <a name="remarks"></a>備註

記憶體檔與磁碟檔一樣。 區別在於,記憶體檔存儲在 RAM 中,而不是存儲在磁碟上。 記憶體檔案可用於快速暫存記憶體,或用於在獨立進程之間傳輸原始位元組或序列化物件。

共用記憶體檔與其他記憶體檔不同,因為記憶體是使用[Global Alloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows 函數分配的。 類`CSharedFile`將資料儲存在全域分配的記憶體區塊中(使用`GlobalAlloc`創建),並且此記憶體區塊可以使用 DDE、剪貼簿或其他 OLE/COM 統一資料傳輸操作(例如`IDataObject`,使用 )共用。

`GlobalAlloc`返回 HGLOBAL 句柄,而不是指向記憶體的指標,例如[malloc](../../c-runtime-library/reference/malloc.md)返回的指標。 某些應用程式需要 HGLOBAL 句柄。 例如,要將數據放在剪貼簿上,您需要一個 HGLOBAL 句柄。

`CSharedFile`不使用記憶體映射的文件,並且數據不能直接在進程之間共用。

`CSharedFile`物件可以自動分配自己的記憶體。 或者,您可以通過調`CSharedFile`用[CSharedFile::setHandle](#sethandle)將您自己的記憶體塊附加到物件。 在這兩種情況下,自動增長記憶體檔的記憶體分配以`nGrowBytes`-大小增量(如果不是零)。 `nGrowBytes`

有關詳細資訊,請參閱運行時*庫參考*[中的 MFC](../../mfc/files-in-mfc.md)和[檔處理](../../c-runtime-library/file-handling.md)中的文章檔。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>需求

**標題:** afxadv.h

## <a name="csharedfilecsharedfile"></a><a name="csharedfile"></a>C 分享檔案:C 分享檔案

構造對`CSharedFile`象並為其分配記憶體。

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>參數

*nAllocFlags*<br/>
指示如何分配記憶體的標誌。 有關有效標誌值的清單,請參閱[GlobalAlloc。](/windows/win32/api/winbase/nf-winbase-globalalloc)

*n 增長位元組*<br/>
記憶體分配以位元組為單位遞增。

## <a name="csharedfiledetach"></a><a name="detach"></a>共用檔案::D

調用此函數以關閉記憶體檔並將其從記憶體塊中分離。

```
HGLOBAL Detach();
```

### <a name="return-value"></a>傳回值

包含記憶體檔內容的記憶體區塊的句柄。

### <a name="remarks"></a>備註

您可以使用**Detach**傳回的句柄呼叫[SetHandle](#sethandle)來重新開啟它。

## <a name="csharedfilesethandle"></a><a name="sethandle"></a>C 分享檔案::設定句柄

調用此函數以將全域記憶體塊附加到`CSharedFile`物件。

```
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>參數

*h全球記憶體*<br/>
處理要附加到的全域記憶體。 `CSharedFile`

*bAllow 增長*<br/>
指定是否允許記憶體塊增長。

### <a name="remarks"></a>備註

如果*bAllowGrow*是非零,則記憶體區塊的大小會根據需要增加,例如,如果您嘗試向檔寫入比記憶體大小更多的字節。

## <a name="see-also"></a>另請參閱

[CMemFile 類別](../../mfc/reference/cmemfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMemFile 類別](../../mfc/reference/cmemfile-class.md)
