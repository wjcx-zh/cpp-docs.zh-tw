---
title: COleStreamFile 類別
ms.date: 11/04/2016
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
ms.openlocfilehash: 1f53d3bd55fbff45257c06af2ab11f066d421a54
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376103"
---
# <a name="colestreamfile-class"></a>COleStreamFile 類別

表示在複合檔案中做為 OLE 結構化儲存體之一部分的資料流 (`IStream`)。

## <a name="syntax"></a>語法

```
class COleStreamFile : public CFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[COleStream 檔案:COleStream 檔案](#colestreamfile)|建構 `COleStreamFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleStream 檔案:附加](#attach)|將流與對象關聯。|
|[COleStream 檔案:建立記憶體](#creatememorystream)|從全域記憶體創建流並將其與對象關聯。|
|[COleStream 檔案:建立串流](#createstream)|創建流並將其與對象關聯。|
|[COleStream檔::D](#detach)|斷開流與物件分離。|
|[COleStream 檔案:取得串流](#getstream)|返回當前流。|
|[COleStream 檔案::開啟串流](#openstream)|安全地打開流並將其與對象關聯。|

## <a name="remarks"></a>備註

必須先`IStorage`存在一個物件,然後才能打開或創建流,除非它是記憶體流。

`COleStreamFile`物件的操作與[CFile](../../mfc/reference/cfile-class.md)物件完全一樣。

有關操作流和存儲的詳細資訊,請參閱文章[「容器:複合檔](../../mfc/containers-compound-files.md)」。

有關詳細資訊,請參閱 Windows SDK 中的[IStream](/windows/win32/api/objidl/nn-objidl-istream)和[IStorage。](/windows/win32/api/objidl/nn-objidl-istorage)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="colestreamfileattach"></a><a name="attach"></a>COleStream 檔案:附加

將提供的 OLE`COleStreamFile`串流與物件關聯。

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>參數

*lpStream*<br/>
指向要與物件關聯的`IStream`OLE 串流 ( )。 不能是 NULL。

### <a name="remarks"></a>備註

物件必須尚未與 OLE 流關聯。

有關詳細資訊,請參閱 Windows SDK 中的[IStream。](/windows/win32/api/objidl/nn-objidl-istream)

## <a name="colestreamfilecolestreamfile"></a><a name="colestreamfile"></a>COleStream 檔案:COleStream 檔案

建立 `COleStreamFile` 物件。

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>參數

*lpStream*<br/>
指向要與物件關聯的 OLE 流的指標。

### <a name="remarks"></a>備註

如果*lpStream*為 NULL,則該物件不與 OLE 流關聯,否則,該物件與提供的 OLE 串流相關聯。

有關詳細資訊,請參閱 Windows SDK 中的[IStream。](/windows/win32/api/objidl/nn-objidl-istream)

## <a name="colestreamfilecreatememorystream"></a><a name="creatememorystream"></a>COleStream 檔案:建立記憶體

安全地從全域共用記憶體中創建新流,其中故障是正常的預期條件。

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*pError*<br/>
指向指示創建操作的完成狀態的[CFileException](../../mfc/reference/cfileexception-class.md)物件或 NULL。 如果要監視嘗試創建流生成的可能異常,請提供此參數。

### <a name="return-value"></a>傳回值

如果成功創建流,則非零;否則 0。

### <a name="remarks"></a>備註

記憶體由 OLE 子系統分配。

有關詳細資訊,請參閱在 Windows SDK 中[創建 StreamOnHGlobal。](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal)

## <a name="colestreamfilecreatestream"></a><a name="createstream"></a>COleStream 檔案:建立串流

在提供的存儲物件中安全地創建新流,其中故障是正常的預期條件。

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*lp 儲存*<br/>
指向包含要建立的流的 OLE 儲存物件。 不能是 NULL。

*lpszStream名稱*<br/>
要創建的流的名稱。 不能是 NULL。

*nOpenFlags*<br/>
打開流時要使用的訪問模式。 預設情況下使用獨佔模式、讀/寫模式和創建模式。 有關可用模式的完整清單,請參閱[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)。

*pError*<br/>
指向[檔案檔案例外](../../mfc/reference/cfileexception-class.md)物件或 NULL。 如果要監視嘗試創建流生成的可能異常,請提供此參數。

### <a name="return-value"></a>傳回值

如果成功創建流,則非零;否則 0。

### <a name="remarks"></a>備註

如果打開失敗,並且*pError*不是 NULL,則將引發文件異常。

有關詳細資訊,請參閱[IStorage::](/windows/win32/api/objidl/nf-objidl-istorage-createstream)在 Windows SDK 中創建流。

## <a name="colestreamfiledetach"></a><a name="detach"></a>COleStream檔::D

在不關閉流的情況下,斷開流與對象分離。

```
LPSTREAM Detach();
```

### <a name="return-value"></a>傳回值

指向與物件關聯的流的指標`IStream`。

### <a name="remarks"></a>備註

在程序終止之前,必須以其他方式關閉流。

有關詳細資訊,請參閱 Windows SDK 中的[IStream。](/windows/win32/api/objidl/nn-objidl-istream)

## <a name="colestreamfilegetstream"></a><a name="getstream"></a>COleStream 檔案:取得串流

調用此函數以返回指向當前流的指標。

```
IStream* GetStream() const;
```

### <a name="return-value"></a>傳回值

指向當前流介面[(IStream)](/windows/win32/api/objidl/nn-objidl-istream)的指標。

## <a name="colestreamfileopenstream"></a><a name="openstream"></a>COleStream 檔案::開啟串流

打開現有流。

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*lp 儲存*<br/>
指向包含要打開的流的 OLE 儲存物件。 不能是 NULL。

*lpszStream名稱*<br/>
要打開的流的名稱。 不能是 NULL。

*nOpenFlags*<br/>
打開流時要使用的訪問模式。 默認情況下使用獨佔和讀/寫模式。 有關可用模式的完整清單,請參閱[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)。

*pError*<br/>
指向[檔案檔案例外](../../mfc/reference/cfileexception-class.md)物件或 NULL。 如果要監視嘗試打開流生成的可能異常,則提供此參數。

### <a name="return-value"></a>傳回值

如果已成功打開流,則非零;否則 0。

### <a name="remarks"></a>備註

如果打開失敗,並且*pError*不是 NULL,則將引發文件異常。

有關詳細資訊,請參閱[IStorage::在](/windows/win32/api/objidl/nf-objidl-istorage-openstream)Windows SDK 中打開流。

## <a name="see-also"></a>另請參閱

[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
