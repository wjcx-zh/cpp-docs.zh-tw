---
title: CMonikerFile 類別
ms.date: 11/04/2016
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
ms.openlocfilehash: 56283b56a1c0832d34ce23c7db47c47d9480aec8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504573"
---
# <a name="cmonikerfile-class"></a>CMonikerFile 類別

表示由[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)命名的資料流程 ( [IStream](/windows/win32/api/objidl/nn-objidl-istream))。

## <a name="syntax"></a>語法

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CMonikerFile:: CMonikerFile](#cmonikerfile)|建構 `CMonikerFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMonikerFile::Close](#close)|卸離並釋放資料流程, 並釋放該名字標記。|
|[CMonikerFile::Detach](#detach)|`IMoniker`從這個`CMonikerFile`物件卸離。|
|[CMonikerFile::GetMoniker](#getmoniker)|傳回目前的標記。|
|[CMonikerFile::Open](#open)|開啟指定的檔案以取得資料流程。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|取得系結內容, 或建立預設已初始化的系結內容。|

## <a name="remarks"></a>備註

標記包含的資訊與檔案的路徑名稱很相似。 如果您有指向標記物件`IMoniker`介面的指標, 您可以存取已識別的檔案, 而不需要任何其他有關檔案實際位置的特定資訊。

衍生自`COleStreamFile`, `CMonikerFile`接受一個名字標記或字串標記法, 它可以放入名字標記中, 並系結至標記為名稱的資料流程。 然後您就可以讀取和寫入該資料流程。 的實際用途`CMonikerFile`是提供對`IStream`所命名之的`IMoniker`簡單存取, 讓您不需要自行系結至資料流程, 但也有`CFile`資料流程的功能。

`CMonikerFile`不能用來系結至資料流程以外的任何專案。 如果您想要系結至儲存體或物件, 則必須直接使用`IMoniker`介面。

如需有關資料流程和名字標記的詳細資訊, 請參閱[COleStreamFile](../../mfc/reference/colestreamfile-class.md) In The *MFC Reference*和[IStream](/windows/win32/api/objidl/nn-objidl-istream) and [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) in the Windows SDK。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>需求

**標頭:** afxole。h

##  <a name="close"></a>CMonikerFile:: Close

呼叫此函式來卸離和釋放資料流程, 並釋放該名字。

```
virtual void Close();
```

### <a name="remarks"></a>備註

可以在未開啟或已關閉的資料流程上呼叫。

##  <a name="cmonikerfile"></a>CMonikerFile:: CMonikerFile

建構 `CMonikerFile` 物件。

```
CMonikerFile();
```

##  <a name="createbindcontext"></a>CMonikerFile:: CreateBindCoNtext

呼叫此函式以建立預設的已初始化系結內容。

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>參數

*pError*<br/>
檔案例外狀況的指標。 發生錯誤時, 會將其設定為原因。

### <a name="return-value"></a>傳回值

如果成功, 則為要系結之系結內容[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)的指標;否則為 Null。 如果實例是以`IBindHost`介面開啟, 則會`IBindHost`從抓取系結內容。 如果沒有`IBindHost`介面, 或介面無法傳回系結內容, 則會建立系結內容。 如需[IBindHost](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\))介面的說明, 請參閱 Windows SDK。

### <a name="remarks"></a>備註

系結內容是一個物件, 它會儲存特定標記系結作業的相關資訊。 您可以覆寫此函式, 以提供自訂系結內容。

##  <a name="detach"></a>CMonikerFile::D etach

呼叫此函式以關閉資料流程。

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*pError*<br/>
檔案例外狀況的指標。 發生錯誤時, 會將其設定為原因。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="getmoniker"></a>CMonikerFile:: GetMoniker

呼叫此函式可取得目前標記的指標。

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>傳回值

目前標記介面的指標 ( [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker))。

### <a name="remarks"></a>備註

因為`CMonikerFile`不是介面, 所以傳回的指標不會遞增參考計數 (透過[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)), 而且會在釋放`CMonikerFile`物件時釋放該標記。 如果您想要保留到名字標記或自行發行, 您必須`AddRef`這麼做。

##  <a name="open"></a>CMonikerFile:: Open

呼叫這個成員函式來開啟檔案或名字物件。

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*lpszURL*<br/>
要開啟之檔案的 URL 或檔案名。

*pError*<br/>
檔案例外狀況的指標。 發生錯誤時, 會將其設定為原因。

*pMoniker*<br/>
要用來取得資料流程之`IMoniker`標記介面的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

*LpszURL*參數不能用在 Macintosh 上。 在 Macintosh上只能使用`Open`的 pMoniker 形式。

您可以使用 URL 或 filename 作為*lpszURL*參數。 例如：

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\-或-

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[COleStreamFile 類別](../../mfc/reference/colestreamfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)
