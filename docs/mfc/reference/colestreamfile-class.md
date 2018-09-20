---
title: COleStreamFile 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f93b367b207730f331e4a9ae16b191f7a5314e4d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399598"
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
|[COleStreamFile::COleStreamFile](#colestreamfile)|建構 `COleStreamFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[COleStreamFile::Attach](#attach)|將資料流與物件產生關聯。|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|從全域記憶體中建立的資料流，並將它與物件相關聯。|
|[COleStreamFile::CreateStream](#createstream)|建立資料流，並將它與物件相關聯。|
|[COleStreamFile::Detach](#detach)|解除關聯之物件的資料流。|
|[COleStreamFile::GetStream](#getstream)|傳回目前資料流。|
|[COleStreamFile::OpenStream](#openstream)|安全地開啟資料流，並將它與物件相關聯。|

## <a name="remarks"></a>備註

`IStorage`物件必須存在才能開啟或建立，除非它是記憶體資料流資料流。

`COleStreamFile` 物件完全相同的操作[CFile](../../mfc/reference/cfile-class.md)物件。

如需有關如何管理資料流和儲存體的詳細資訊，請參閱[容器： 複合檔案](../../mfc/containers-compound-files.md)...

如需詳細資訊，請參閱 < [IStream](/windows/desktop/api/objidl/nn-objidl-istream)並[IStorage](/windows/desktop/api/objidl/nn-objidl-istorage) Windows SDK 中。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>需求

**標頭：** afxole.h

##  <a name="attach"></a>  COleStreamFile::Attach

將使用提供的 OLE 資料流`COleStreamFile`物件。

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>參數

*lpStream*<br/>
指向 OLE 資料流 (`IStream`) 與物件相關聯。 不可以是 NULL。

### <a name="remarks"></a>備註

物件已經不可與 OLE 資料流相關聯。

如需詳細資訊，請參閱 < [IStream](/windows/desktop/api/objidl/nn-objidl-istream) Windows SDK 中。

##  <a name="colestreamfile"></a>  COleStreamFile::COleStreamFile

建立 `COleStreamFile` 物件。

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>參數

*lpStream*<br/>
要與物件相關聯之 OLE 資料流指標。

### <a name="remarks"></a>備註

如果*lpStream*是 NULL，物件不是與 OLE 資料流相關聯，否則物件與提供的 OLE 資料流相關聯。

如需詳細資訊，請參閱 < [IStream](/windows/desktop/api/objidl/nn-objidl-istream) Windows SDK 中。

##  <a name="creatememorystream"></a>  COleStreamFile::CreateMemoryStream

安全地建立新的資料流通用的共用記憶體不足，失敗情形是一般的預期。

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*pError*<br/>
指向[CFileException](../../mfc/reference/cfileexception-class.md)物件或 NULL，表示建立作業的完成狀態。 如果您想要監視產生的嘗試建立資料流的可能例外狀況，請提供這個參數。

### <a name="return-value"></a>傳回值

如果成功，建立資料流，非零值。否則為 0。

### <a name="remarks"></a>備註

OLE 子系統所配置記憶體。

如需詳細資訊，請參閱 < [CreateStreamOnHGlobal](/windows/desktop/api/combaseapi/nf-combaseapi-createstreamonhglobal) Windows SDK 中。

##  <a name="createstream"></a>  COleStreamFile::CreateStream

安全地建立新的資料流，其中失敗情形是一般的預期提供的儲存體物件中。

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*lpStorage*<br/>
指向包含要建立的資料流的 OLE 儲存體物件。 不可以是 NULL。

*lpszStreamName*<br/>
要建立之資料流的名稱。 不可以是 NULL。

*nOpenFlags*<br/>
開啟資料流時要使用的存取模式。 獨佔、 讀取/寫入，並建立模式由預設值。 可用的模式的完整清單，請參閱 < [CFile::CFile](../../mfc/reference/cfile-class.md#cfile)。

*pError*<br/>
指向[CFileException](../../mfc/reference/cfileexception-class.md)物件或 NULL。 如果您想要監視產生的嘗試建立資料流的可能例外狀況，請提供這個參數。

### <a name="return-value"></a>傳回值

如果成功，建立資料流，非零值。否則為 0。

### <a name="remarks"></a>備註

如果開啟失敗檔案例外狀況將會擲回並*pError*不是 NULL。

如需詳細資訊，請參閱 < [IStorage::CreateStream](/windows/desktop/api/objidl/nf-objidl-istorage-createstream) Windows SDK 中。

##  <a name="detach"></a>  COleStreamFile::Detach

解除關聯物件的資料流，而不需要關閉資料流。

```
LPSTREAM Detach();
```

### <a name="return-value"></a>傳回值

資料流的指標 (`IStream`) 是與物件相關聯。

### <a name="remarks"></a>備註

程式終止之前，必須透過其他方式關閉資料流。

如需詳細資訊，請參閱 < [IStream](/windows/desktop/api/objidl/nn-objidl-istream) Windows SDK 中。

##  <a name="getstream"></a>  COleStreamFile::GetStream

呼叫此函式可傳回目前資料流的指標。

```
IStream* GetStream() const;
```

### <a name="return-value"></a>傳回值

目前的資料流介面的指標 ( [IStream](/windows/desktop/api/objidl/nn-objidl-istream))。

##  <a name="openstream"></a>  COleStreamFile::OpenStream

開啟現有的資料流。

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*lpStorage*<br/>
指向包含要開啟的資料流的 OLE 儲存體物件。 不可以是 NULL。

*lpszStreamName*<br/>
若要開啟資料流名稱。 不可以是 NULL。

*nOpenFlags*<br/>
開啟資料流時要使用的存取模式。 專有和讀/寫模式所使用預設值。 可用的模式的完整清單，請參閱[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)。

*pError*<br/>
指向[CFileException](../../mfc/reference/cfileexception-class.md)物件或 NULL。 如果您想要監視可能嘗試開啟資料流所產生的例外狀況，請提供這個參數。

### <a name="return-value"></a>傳回值

如果成功; 開啟資料流，則為非零否則為 0。

### <a name="remarks"></a>備註

如果開啟失敗檔案例外狀況將會擲回並*pError*不是 NULL。

如需詳細資訊，請參閱 < [IStorage::OpenStream](/windows/desktop/api/objidl/nf-objidl-istorage-openstream) Windows SDK 中。

## <a name="see-also"></a>另請參閱

[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)



