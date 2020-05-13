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
ms.openlocfilehash: fc74ad2499fcde63faa2c5859a87fd9ffd2846eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319778"
---
# <a name="cmonikerfile-class"></a>CMonikerFile 類別

表示由[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)命名的資料串流( [IStream](/windows/win32/api/objidl/nn-objidl-istream))。

## <a name="syntax"></a>語法

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMoniker 檔案:CMoniker 檔案](#cmonikerfile)|建構 `CMonikerFile` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMoniker 檔案:關閉](#close)|分離並釋放流並釋放名字物件。|
|[CMoniker檔::D](#detach)|從`CMonikerFile`物件`IMoniker`分離 。|
|[CMoniker 檔:取得莫尼克爾](#getmoniker)|返回當前名字物件。|
|[CMoniker 檔::開啟](#open)|開啟指定的檔案以取得流。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMoniker 檔案:建立連結中文](#createbindcontext)|獲取繫結上下文或創建預設初始化綁定上下文。|

## <a name="remarks"></a>備註

名字物件包含的信息與檔的路徑名稱非常類似。 如果具有指向名字物件介面的`IMoniker`指標,則可以造訪已標識的檔,而無需提供有關文件實際位置的任何其他特定資訊。

派生自`COleStreamFile``CMonikerFile`,獲取可以將其轉換為名字物件並綁定到名字物件為名稱的流的字串表示形式。 然後,您可以讀取和寫入該流。 的真正目的是`CMonikerFile`提供對`IStream``IMoniker`s 命名的 s 的簡單存取,這樣您不必自己綁定到流`CFile`,而又對流具有功能。

`CMonikerFile`不能用於綁定到流以外的任何內容。 如果要結合到儲存或物件,必須直接使用介面`IMoniker`。

有關流和名字的詳細資訊,請參閱*MFC 參考*中的[COleStreamFile](../../mfc/reference/colestreamfile-class.md)以及 Windows SDK 中的[IStream](/windows/win32/api/objidl/nn-objidl-istream)和[IMoniker。](/windows/win32/api/objidl/nn-objidl-imoniker)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStream 檔案](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>需求

**標題:** afxole.h

## <a name="cmonikerfileclose"></a><a name="close"></a>CMoniker 檔案:關閉

調用此函數以分離和釋放流並釋放名字物件。

```
virtual void Close();
```

### <a name="remarks"></a>備註

可以在未打開或已關閉的流上調用。

## <a name="cmonikerfilecmonikerfile"></a><a name="cmonikerfile"></a>CMoniker 檔案:CMoniker 檔案

建構 `CMonikerFile` 物件。

```
CMonikerFile();
```

## <a name="cmonikerfilecreatebindcontext"></a><a name="createbindcontext"></a>CMoniker 檔案:建立連結中文

呼叫此函數以創建預設初始化綁定上下文。

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>參數

*pError*<br/>
指向文件異常的指標。 如果出現錯誤,它將設置為原因。

### <a name="return-value"></a>傳回值

指向綁定上下文 IBindCtx 的指標,如果成功,則與綁定上下文[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)綁定;否則 NULL。 如果實體是使用介面開啟的`IBindHost`,則從中檢索繫結上下文`IBindHost`。 如果沒有`IBindHost`介面或介面無法返回綁定上下文,則創建綁定上下文。 有關[IBindHost](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\))介面的說明,請參閱Windows SDK。

### <a name="remarks"></a>備註

綁定上下文是存儲有關特定名字綁定操作的資訊物件。 您可以重寫此函數以提供自定義綁定上下文。

## <a name="cmonikerfiledetach"></a><a name="detach"></a>CMoniker檔::D

調用此函數以關閉流。

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*pError*<br/>
指向文件異常的指標。 如果出現錯誤,它將設置為原因。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

## <a name="cmonikerfilegetmoniker"></a><a name="getmoniker"></a>CMoniker 檔:取得莫尼克爾

呼叫此函數以檢索指向當前名字物件的指標。

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>傳回值

指向當前名字介面[(IMoniker) 的](/windows/win32/api/objidl/nn-objidl-imoniker)指標。

### <a name="remarks"></a>備註

由於`CMonikerFile`不是介面,返回的指標不會增加引用計數(通過[AddRef),](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)並且`CMonikerFile`在釋放 物件時釋放名字物件。 如果你想抓住名字或釋放它自己,你必須`AddRef`它。

## <a name="cmonikerfileopen"></a><a name="open"></a>CMoniker 檔::開啟

呼叫此成員函數以打開檔案或名字物件。

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
要打開的檔案的 URL 或檔名。

*pError*<br/>
指向文件異常的指標。 如果出現錯誤,它將設置為原因。

*普莫尼克爾*<br/>
指向用於獲取流的名字介面`IMoniker`的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

*lpszURL*參數不能在 Macintosh 上使用。 只有*pMoniker*的`Open`格式可以在 Macintosh 上使用。

可以使用 URL 或檔名進行*lpszURL*參數。 例如：

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- 或 -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>另請參閱

[COleStreamFile 類別](../../mfc/reference/colestreamfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile 類別](../../mfc/reference/casyncmonikerfile-class.md)
