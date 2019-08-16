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
ms.openlocfilehash: 96e8fee71f02ea750fd8b33f41fd2fd517e9081e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503693"
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
|[COleStreamFile:: COleStreamFile](#colestreamfile)|建構 `COleStreamFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleStreamFile::Attach](#attach)|將資料流程與物件產生關聯。|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|從全域記憶體建立資料流程, 並將它與物件產生關聯。|
|[COleStreamFile::CreateStream](#createstream)|建立資料流程, 並將它與物件產生關聯。|
|[COleStreamFile::Detach](#detach)|解除資料流程與物件的的比對。|
|[COleStreamFile::GetStream](#getstream)|傳回目前的資料流程。|
|[COleStreamFile::OpenStream](#openstream)|安全地開啟資料流程, 並將它與物件產生關聯。|

## <a name="remarks"></a>備註

`IStorage`物件必須存在, 才能開啟或建立資料流程, 除非它是記憶體資料流程。

`COleStreamFile`物件的操作方式與[CFile](../../mfc/reference/cfile-class.md)物件完全相同。

如需運算元據流和儲存體的詳細資訊, 請參閱[容器:複合檔案](../../mfc/containers-compound-files.md)。

如需詳細資訊, 請參閱 Windows SDK 中的[IStream](/windows/win32/api/objidl/nn-objidl-istream)和[IStorage](/windows/win32/api/objidl/nn-objidl-istorage) 。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>需求

**標頭:** afxole。h

##  <a name="attach"></a>COleStreamFile:: Attach

將提供的 OLE 資料流程與`COleStreamFile`物件產生關聯。

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>參數

*lpStream*<br/>
指向要與物件相關聯`IStream`的 OLE 資料流程 ()。 不可以是 NULL。

### <a name="remarks"></a>備註

物件必須尚未與 OLE 資料流程相關聯。

如需詳細資訊, 請參閱 Windows SDK 中的[IStream](/windows/win32/api/objidl/nn-objidl-istream) 。

##  <a name="colestreamfile"></a>COleStreamFile:: COleStreamFile

建立 `COleStreamFile` 物件。

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>參數

*lpStream*<br/>
要與物件相關聯之 OLE 資料流程的指標。

### <a name="remarks"></a>備註

如果*lpStream*為 Null, 則物件不會與 ole 資料流程相關聯, 否則物件會與提供的 ole 資料流程相關聯。

如需詳細資訊, 請參閱 Windows SDK 中的[IStream](/windows/win32/api/objidl/nn-objidl-istream) 。

##  <a name="creatememorystream"></a>COleStreamFile:: CreateMemoryStream

安全地從全域共用記憶體建立新的資料流程, 其中失敗是正常且預期的狀況。

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*pError*<br/>
指向[CFileException](../../mfc/reference/cfileexception-class.md)物件或 Null, 表示建立作業的完成狀態。 如果您想要監視嘗試建立資料流程所產生的可能例外狀況, 請提供此參數。

### <a name="return-value"></a>傳回值

如果成功建立資料流程, 則為非零;否則為0。

### <a name="remarks"></a>備註

記憶體是由 OLE 子系統配置。

如需詳細資訊, 請參閱 Windows SDK 中的[CreateStreamOnHGlobal](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal) 。

##  <a name="createstream"></a>COleStreamFile:: CreateStream

在提供的儲存物件中安全地建立新的資料流程, 其中失敗是正常的預期狀況。

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*lpStorage*<br/>
指向包含要建立之資料流程的 OLE 儲存物件。 不可以是 NULL。

*lpszStreamName*<br/>
要建立之資料流程的名稱。 不可以是 NULL。

*nOpenFlags*<br/>
開啟資料流程時要使用的存取模式。 預設會使用 [獨佔]、[讀取/寫入] 和 [建立] 模式。 如需可用模式的完整清單, 請參閱[CFile:: CFile](../../mfc/reference/cfile-class.md#cfile)。

*pError*<br/>
指向[CFileException](../../mfc/reference/cfileexception-class.md)物件或 Null。 如果您想要監視嘗試建立資料流程所產生的可能例外狀況, 請提供此參數。

### <a name="return-value"></a>傳回值

如果成功建立資料流程, 則為非零;否則為0。

### <a name="remarks"></a>備註

如果 open 失敗且*pError*不是 Null, 則會擲回檔案例外狀況。

如需詳細資訊, 請參閱 Windows SDK 中的[IStorage:: CreateStream](/windows/win32/api/objidl/nf-objidl-istorage-createstream) 。

##  <a name="detach"></a>COleStreamFile::D etach

解除資料流程與物件的比對, 而不關閉資料流程。

```
LPSTREAM Detach();
```

### <a name="return-value"></a>傳回值

與物件相關聯之資料流程`IStream`() 的指標。

### <a name="remarks"></a>備註

在程式終止之前, 必須以其他方式關閉資料流程。

如需詳細資訊, 請參閱 Windows SDK 中的[IStream](/windows/win32/api/objidl/nn-objidl-istream) 。

##  <a name="getstream"></a>COleStreamFile:: GetStream

呼叫此函式可傳回目前資料流程的指標。

```
IStream* GetStream() const;
```

### <a name="return-value"></a>傳回值

目前資料流程介面 ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)) 的指標。

##  <a name="openstream"></a>COleStreamFile:: OpenStream

開啟現有的資料流程。

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*lpStorage*<br/>
指向包含要開啟之資料流程的 OLE 儲存物件。 不可以是 NULL。

*lpszStreamName*<br/>
要開啟的資料流程名稱。 不可以是 NULL。

*nOpenFlags*<br/>
開啟資料流程時要使用的存取模式。 預設會使用獨佔和讀取/寫入模式。 如需可用模式的完整清單, 請參閱[CFile:: CFile](../../mfc/reference/cfile-class.md#cfile)。

*pError*<br/>
指向[CFileException](../../mfc/reference/cfileexception-class.md)物件或 Null。 如果您想要監視嘗試開啟資料流程而產生的可能例外狀況, 請提供此參數。

### <a name="return-value"></a>傳回值

如果成功開啟資料流程, 則為非零;否則為0。

### <a name="remarks"></a>備註

如果 open 失敗且*pError*不是 Null, 則會擲回檔案例外狀況。

如需詳細資訊, 請參閱 Windows SDK 中的[IStorage:: OpenStream](/windows/win32/api/objidl/nf-objidl-istorage-openstream) 。

## <a name="see-also"></a>另請參閱

[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
