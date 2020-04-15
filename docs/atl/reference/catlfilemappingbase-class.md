---
title: CAtlFile對應基質
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
ms.openlocfilehash: ae790cf1248c78ff9aa70c0e586f86af6c8f3b9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318947"
---
# <a name="catlfilemappingbase-class"></a>CAtlFile對應基質

此類表示記憶體映射的檔。

> [!IMPORTANT]
> 此類及其成員不能在Windows運行時中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
class CAtlFileMappingBase
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CAtl 檔案映射庫::CAtlFile映射庫](#catlfilemappingbase)|建構函式。|
|[CAtl檔案對應庫::_CAtlFile映射庫](#dtor)|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAtlFile對應基礎::從](#copyfrom)|呼叫此方法從檔映射物件複製。|
|[CAtlFile 對應基礎:抓取資料](#getdata)|呼叫此方法從檔映射對象獲取資料。|
|[CAtlFile對應基礎::取得手柄](#gethandle)|調用此方法以返回檔句柄。|
|[CAtlFile對應基礎::抓取對應大小](#getmappingsize)|呼叫此方法從檔映射對象獲取映射大小。|
|[CAtlFile 對應基礎:地圖檔](#mapfile)|呼叫此方法以建立檔映射物件。|
|[CAtlFile對應基礎::映射共用Mem](#mapsharedmem)|呼叫此方法以建立允許完全存取所有進程的檔映射物件。|
|[CAtlFile對應基礎:開啟映射](#openmapping)|呼叫此方法以將句柄返回到檔映射物件。|
|[CAtlFile對應基礎::取消映射](#unmap)|呼叫此方法以取消映射檔映射物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CAtlFile映射基礎::運算符 |](#operator_eq)|將目前檔案對應物件設定到另一個檔對應物件。|

## <a name="remarks"></a>備註

檔案映射是檔內容與進程虛擬位址空間的一部分的關聯。 此類提供了創建檔映射物件的方法,允許程式輕鬆存取和共享資料。

有關詳細資訊,請參閱 Windows SDK[中的檔案映射](/windows/win32/Memory/file-mapping)。

## <a name="requirements"></a>需求

**標題:** atlfile.h

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="catlfilemappingbase"></a>CAtl 檔案映射庫::CAtlFile映射庫

建構函式。

```
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>參數

*奧裡格*<br/>
要複製的原始檔映射物件以創建新物件。

### <a name="remarks"></a>備註

建立新的檔案映射物件,可以選擇使用現有物件。 仍需要調用[CAtlFileMappingBase:mapFile](#mapfile)來打開或創建特定檔的檔映射物件。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="dtor"></a>CAtl檔案對應庫::_CAtlFile映射庫

解構函式。

```
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>備註

釋放類分配的任何資源,並調用[CAtlFileMappingBase::unmap](#unmap)方法。

## <a name="catlfilemappingbasecopyfrom"></a><a name="copyfrom"></a>CAtlFile對應基礎::從

呼叫此方法從檔映射物件複製。

```
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>參數

*奧裡格*<br/>
要複製的原始檔映射物件。

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

## <a name="catlfilemappingbasegetdata"></a><a name="getdata"></a>CAtlFile 對應基礎:抓取資料

呼叫此方法從檔映射對象獲取資料。

```
void* GetData() const throw();
```

### <a name="return-value"></a>傳回值

返回指向數據的指標。

## <a name="catlfilemappingbasegethandle"></a><a name="gethandle"></a>CAtlFile對應基礎::取得手柄

呼叫此方法以將句柄返回到檔映射物件。

```
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>傳回值

返回檔映射物件的句柄。

## <a name="catlfilemappingbasegetmappingsize"></a><a name="getmappingsize"></a>CAtlFile對應基礎::抓取對應大小

呼叫此方法從檔映射對象獲取映射大小。

```
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>傳回值

返回映射大小。

### <a name="example"></a>範例

請參考[CAtlFile 映射庫的範例:CAtlFile 映射庫](#catlfilemappingbase)。

## <a name="catlfilemappingbasemapfile"></a><a name="mapfile"></a>CAtlFile 對應基礎:地圖檔

呼叫此方法以開啟或建立指定檔案的檔案映射物件。

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
處理從中創建映射物件的檔。 *hFile*必須有效且不能設置為INVALID_HANDLE_VALUE。

*n 對應大小*<br/>
映射大小。 如果為 0,則檔映射物件的最大大小等於*hFile*標識的檔的當前大小。

*n位移*<br/>
要開始映射的檔偏移量。 偏移值必須是系統記憶體分配粒度的倍數。

*dwMapping保護*<br/>
映射檔時檔視圖所需的保護。 請參考 Windows SDK[建立檔案映射](/windows/win32/api/winbase/nf-winbase-createfilemappinga)中的*fl 保護*。

*dwView 希望存取*<br/>
指定存取檔案檢視的類型,因此,指定檔映射的頁面的保護。 在 Windows SDK 中的[MapViewFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)中查看*dwdAccess。*

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

建立檔案映射物件後,檔的大小不得超過檔映射物件的大小;如果是,則並非所有文件的內容都可供共用。 有關詳細資訊,請參閱在 Windows SDK 中[創建檔映射](/windows/win32/api/winbase/nf-winbase-createfilemappinga)和[MapViewFileEx。](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)

### <a name="example"></a>範例

請參考[CAtlFile 映射庫的範例:CAtlFile 映射庫](#catlfilemappingbase)。

## <a name="catlfilemappingbasemapsharedmem"></a><a name="mapsharedmem"></a>CAtlFile對應基礎::映射共用Mem

呼叫此方法以建立允許完全存取所有進程的檔映射物件。

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

*n 對應大小*<br/>
映射大小。 如果為 0,則檔映射物件的最大大小等於*szName*標識的檔映射物件的當前大小。

*szName*<br/>
映射物件的名稱。

*pb 已存在*<br/>
指向如果映射物件已存在,則設置為 TRUE 的 BOOL 值。

*lpsa*<br/>
指向結構的`SECURITY_ATTRIBUTES`指標,用於確定返回的句柄是否可以由子進程繼承。 請參考 Windows SDK[建立檔案映射](/windows/win32/api/winbase/nf-winbase-createfilemappinga)中的*lp 屬性*。

*dwMapping保護*<br/>
映射檔時檔視圖所需的保護。 請參閱*flProtect*Windows `CreateFileMapping` SDK 中的 fl 保護。

*dwView 希望存取*<br/>
指定存取檔案檢視的類型,因此,指定檔映射的頁面的保護。 在 Windows SDK 中的[MapViewFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)中查看*dwdAccess。*

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

`MapShareMem`允許在進程之間共用由[CreateFileMapping](/windows/win32/api/winbase/nf-winbase-createfilemappinga)創建的現有檔映射物件。

## <a name="catlfilemappingbaseopenmapping"></a><a name="openmapping"></a>CAtlFile對應基礎:開啟映射

呼叫此方法以開啟指定檔案的命名檔案映射物件。

```
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>參數

*szName*<br/>
映射物件的名稱。 如果此名稱對檔映射物件有打開的句柄,並且映射物件上的安全描述符不與*dwView希望訪問*參數衝突,則打開操作將成功。

*n 對應大小*<br/>
映射大小。 如果為 0,則檔映射物件的最大大小等於*szName*標識的檔映射物件的當前大小。

*n位移*<br/>
要開始映射的檔偏移量。 偏移值必須是系統記憶體分配粒度的倍數。

*dwView 希望存取*<br/>
指定存取檔案檢視的類型,因此,指定檔映射的頁面的保護。 在 Windows SDK 中的[MapViewFileEx](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex)中查看*dwdAccess。*

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

在調試生成中,如果輸入參數無效,將發生斷言錯誤。

## <a name="catlfilemappingbaseoperator-"></a><a name="operator_eq"></a>CAtlFile映射基礎::運算符 |

將目前檔案對應物件設定到另一個檔對應物件。

```
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>參數

*奧裡格*<br/>
當前檔映射物件。

### <a name="return-value"></a>傳回值

返回對當前物件的引用。

## <a name="catlfilemappingbaseunmap"></a><a name="unmap"></a>CAtlFile對應基礎::取消映射

呼叫此方法以取消映射檔映射物件。

```
HRESULT Unmap() throw();
```

### <a name="return-value"></a>傳回值

返回成功S_OK,或失敗時返回錯誤 HRESULT。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[「取消映射查看檔](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile)」 。

## <a name="see-also"></a>另請參閱

[CAtl 檔案映射類別](../../atl/reference/catlfilemapping-class.md)<br/>
[類別概觀](../../atl/atl-class-overview.md)
