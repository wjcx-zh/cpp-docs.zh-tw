---
title: CAtlFileMappingBase 類別
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CopyFrom
- ATLFILE/ATL::CAtlFileMappingBase::GetData
- ATLFILE/ATL::CAtlFileMappingBase::GetHandle
- ATLFILE/ATL::CAtlFileMappingBase::GetMappingSize
- ATLFILE/ATL::CAtlFileMappingBase::MapFile
- ATLFILE/ATL::CAtlFileMappingBase::MapSharedMem
- ATLFILE/ATL::CAtlFileMappingBase::OpenMapping
- ATLFILE/ATL::CAtlFileMappingBase::Unmap
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
ms.openlocfilehash: 3d9627c7a19cccc0cd3aec46d71b23c8a84711bf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497776"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase 類別

此類別代表記憶體對應檔。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAtlFileMappingBase
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|建構函式。|
|[CAtlFileMappingBase:: ~ CAtlFileMappingBase](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlFileMappingBase::CopyFrom](#copyfrom)|呼叫這個方法, 從檔案對應物件複製。|
|[CAtlFileMappingBase::GetData](#getdata)|呼叫這個方法, 以從檔案對應物件取得資料。|
|[CAtlFileMappingBase::GetHandle](#gethandle)|呼叫這個方法, 以傳回檔案控制代碼。|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|呼叫這個方法, 以從檔案對應物件取得對應大小。|
|[CAtlFileMappingBase::MapFile](#mapfile)|呼叫這個方法來建立檔案對應物件。|
|[CAtlFileMappingBase::MapSharedMem](#mapsharedmem)|呼叫這個方法來建立檔案對應物件, 以允許所有進程的完整存取權。|
|[CAtlFileMappingBase::OpenMapping](#openmapping)|呼叫這個方法, 以傳回檔案對應物件的控制碼。|
|[CAtlFileMappingBase::Unmap](#unmap)|呼叫這個方法可取消對應檔案對應物件。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CAtlFileMappingBase:: operator =](#operator_eq)|將目前的檔案對應物件設定為另一個檔案對應物件。|

## <a name="remarks"></a>備註

檔案對應是指檔案內容與進程的虛擬位址空間部分的關聯。 這個類別會提供建立檔案對應物件的方法, 讓程式能夠輕鬆地存取及共用資料。

如需詳細資訊, 請參閱 Windows SDK 中的檔案[對應](/windows/win32/Memory/file-mapping)。

## <a name="requirements"></a>需求

**標頭:** atlfile。h

##  <a name="catlfilemappingbase"></a>CAtlFileMappingBase::CAtlFileMappingBase

建構函式。

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>參數

*orig*<br/>
要複製的原始檔案對應物件, 用來建立新的物件。

### <a name="remarks"></a>備註

建立新的檔案對應物件, 並選擇性地使用現有的物件。 您仍然必須呼叫[CAtlFileMappingBase::](#mapfile) mapping, 才能開啟或建立特定檔案的檔案對應物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

##  <a name="dtor"></a>CAtlFileMappingBase:: ~ CAtlFileMappingBase

解構函式。

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>備註

釋放類別所配置的任何資源, 並呼叫[CAtlFileMappingBase::](#unmap)取消對應方法。

##  <a name="copyfrom"></a>CAtlFileMappingBase:: CopyFrom

呼叫這個方法, 從檔案對應物件複製。

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>參數

*orig*<br/>
複製來源的原始檔案對應物件。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

##  <a name="getdata"></a>CAtlFileMappingBase:: 操作

呼叫這個方法, 以從檔案對應物件取得資料。

```
void* GetData() const throw();
```

### <a name="return-value"></a>傳回值

傳回資料的指標。

##  <a name="gethandle"></a>CAtlFileMappingBase:: GetHandle

呼叫這個方法, 以傳回檔案對應物件的控制碼。

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>傳回值

傳回檔案對應物件的控制碼。

##  <a name="getmappingsize"></a>CAtlFileMappingBase::GetMappingSize

呼叫這個方法, 以從檔案對應物件取得對應大小。

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>傳回值

傳回對應大小。

### <a name="example"></a>範例

請參閱[CAtlFileMappingBase:: CAtlFileMappingBase](#catlfilemappingbase)的範例。

##  <a name="mapfile"></a>CAtlFileMappingBase:: 對應檔

呼叫這個方法, 為指定的檔案開啟或建立檔案對應物件。

```
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>參數

*hFile*<br/>
用來建立對應物件之檔案的控制碼。 *hFile*必須是有效的, 而且不能設定為 INVALID_HANDLE_VALUE。

*nMappingSize*<br/>
對應大小。 如果為 0, 則表示檔案對應物件的大小上限等於 HFile 所識別之檔案的目前大小 *。*

*nOffset*<br/>
要開始對應的檔案位移。 Offset 值必須是系統記憶體配置資料細微性的倍數。

*dwMappingProtection*<br/>
檔案對應時, 檔案視圖所需的保護。 請參閱 Windows SDK 中[CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappingw)的*flProtect* 。

*dwViewDesiredAccess*<br/>
指定檔案視圖的存取類型, 並因此保護檔案所對應的頁面。 請參閱 Windows SDK 中[MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)的*dwDesiredAccess* 。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

建立檔案對應物件之後, 檔案的大小不能超過檔案對應物件的大小;如果有, 則不是所有檔案的內容都可以共用。 如需詳細資訊, 請參閱 Windows SDK 中的[CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappingw)和[MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) 。

### <a name="example"></a>範例

請參閱[CAtlFileMappingBase:: CAtlFileMappingBase](#catlfilemappingbase)的範例。

##  <a name="mapsharedmem"></a>CAtlFileMappingBase::MapSharedMem

呼叫這個方法來建立檔案對應物件, 以允許所有進程的完整存取權。

```
HRESULT MapSharedMem(
    SIZE_T nMappingSize,
    LPCTSTR szName,
    BOOL* pbAlreadyExisted = NULL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    DWORD dwMappingProtection = PAGE_READWRITE,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>參數

*nMappingSize*<br/>
對應大小。 如果為 0, 則表示檔案對應物件的大小上限等於*szName*所識別之檔案對應物件的目前大小。

*szName*<br/>
對應物件的名稱。

*pbAlreadyExisted*<br/>
如果對應物件已經存在, 則指向設定為 TRUE 的 BOOL 值。

*lpsa*<br/>
`SECURITY_ATTRIBUTES`結構的指標, 判斷子進程是否可以繼承傳回的控制碼。 請參閱 Windows SDK 中[CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappingw)的*lpAttributes* 。

*dwMappingProtection*<br/>
檔案進行對應時, 檔案視圖所需的保護。 請參閱 Windows SDK `CreateFileMapping`中的 flProtect。

*dwViewDesiredAccess*<br/>
指定檔案視圖的存取類型, 並因此保護檔案所對應的頁面。 請參閱 Windows SDK 中[MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)的*dwDesiredAccess* 。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

`MapShareMem`允許在進程之間共用現有的檔案對應物件 (由[CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappingw)建立)。

##  <a name="openmapping"></a>CAtlFileMappingBase::OpenMapping

呼叫這個方法, 為指定的檔案開啟命名的檔案對應物件。

```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>參數

*szName*<br/>
對應物件的名稱。 如果這個名稱有檔案對應物件的開啟控制碼, 而且對應物件上的安全描述項與*dwViewDesiredAccess*參數不衝突, 則開啟的作業會成功。

*nMappingSize*<br/>
對應大小。 如果為 0, 則表示檔案對應物件的大小上限等於*szName*所識別之檔案對應物件的目前大小。

*nOffset*<br/>
要開始對應的檔案位移。 Offset 值必須是系統記憶體配置資料細微性的倍數。

*dwViewDesiredAccess*<br/>
指定檔案視圖的存取類型, 並因此保護檔案所對應的頁面。 請參閱 Windows SDK 中[MapViewOfFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)的*dwDesiredAccess* 。

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

在「偵錯工具組建」中, 如果輸入參數無效, 就會發生判斷提示錯誤。

##  <a name="operator_eq"></a>CAtlFileMappingBase:: operator =

將目前的檔案對應物件設定為另一個檔案對應物件。

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>參數

*orig*<br/>
目前的檔案對應物件。

### <a name="return-value"></a>傳回值

傳回目前物件的參考。

##  <a name="unmap"></a>CAtlFileMappingBase:: 取消對應

呼叫這個方法可取消對應檔案對應物件。

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>傳回值

在成功時傳回 S_OK, 或在失敗時傳回錯誤 HRESULT。

### <a name="remarks"></a>備註

如需詳細資訊, 請參閱 Windows SDK 中的[UnmapViewOfFile](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile) 。

## <a name="see-also"></a>另請參閱

[CAtlFileMapping 類別](../../atl/reference/catlfilemapping-class.md)<br/>
[類別總覽](../../atl/atl-class-overview.md)
