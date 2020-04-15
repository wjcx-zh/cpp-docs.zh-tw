---
title: CFileException 類別
ms.date: 11/04/2016
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
helpviewer_keywords:
- CFileException [MFC], CFileException
- CFileException [MFC], ErrnoToException
- CFileException [MFC], GetErrorMessage
- CFileException [MFC], OsErrorToException
- CFileException [MFC], ThrowErrno
- CFileException [MFC], ThrowOsError
- CFileException [MFC], m_cause
- CFileException [MFC], m_lOsError
- CFileException [MFC], m_strFileName
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
ms.openlocfilehash: 2d1025ca33d5641982ba52f1ac539db85df3bfd5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373885"
---
# <a name="cfileexception-class"></a>CFileException 類別

表示檔案相關的例外狀況。

## <a name="syntax"></a>語法

```
class CFileException : public CException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[檔案例外:檔案例外](#cfileexception)|建構 `CFileException` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[檔案例外::錯誤例外](#errnotoexception)|返回與運行時錯誤編號對應的原因代碼。|
|[檔案例外:抓取錯誤訊息](#geterrormessage)|檢索描述異常的消息。|
|[檔案例外::錯誤例外](#oserrortoexception)|返回與作業系統錯誤代碼對應的原因代碼。|
|[檔例外::ThrowErrno](#throwerrno)|根據運行時錯誤編號引發文件異常。|
|[檔案例外::拋擲錯誤](#throwoserror)|根據操作系統錯誤編號引發文件異常。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[檔案例外::m_cause](#m_cause)|包含與異常原因對應的可移植代碼。|
|[檔案例外:m_lOsError](#m_loserror)|包含相關的作業系統錯誤編號。|
|[檔案例外:m_strFileName](#m_strfilename)|包含此異常的檔名稱。|

## <a name="remarks"></a>備註

該`CFileException`類包括保存可移植原因代碼和作業系統特定錯誤編號的公共數據成員。 該類還提供靜態成員函數,用於引發文件異常,以及返回作業系統錯誤和 C 運行時錯誤的原因代碼。

`CFileException`物件在源類的成員函數`CFile`和成員函數中構造和引發。 您可以在**CATCH**表達式的範圍內訪問這些物件。 對於可移植性,請僅使用原因代碼來獲取異常原因。 有關異常的詳細資訊,請參閱異常[處理 (MFC) 一](../../mfc/exception-handling-in-mfc.md)文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="cfileexceptioncfileexception"></a><a name="cfileexception"></a>檔案例外:檔案例外

建構一個`CFileException`物件,該物件將原因代碼和操作系統代碼存儲在物件中。

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>參數

*cause*<br/>
指示異常原因的枚舉類型變數。 有關可能值的清單,請參閱[CFileException::m_cause。](#m_cause)

*LOsError*<br/>
異常的特定於操作系統的原因(如果可用)。 *lOsError*參數提供的資訊比*原因*多。

*lpsz 壓縮檔名稱*<br/>
指向包含引起異常`CFile`的物件名稱的字串。

### <a name="remarks"></a>備註

不要直接使用此建構函數,而是呼叫全域函數[AfxThrowFileException](exception-processing.md#afxthrowfileexception)。

> [!NOTE]
> 變數*lOsError*僅`CFile`適用於`CStdioFile`和 物件。 類`CMemFile`不處理此錯誤代碼。

## <a name="cfileexceptionerrnotoexception"></a><a name="errnotoexception"></a>檔案例外::錯誤例外

將給定的運行時庫錯誤值轉換為`CFileException`枚舉錯誤值。

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>參數

*內埃爾諾*<br/>
運行時定義的整數錯誤代碼包括檔 ERRNO。H。

### <a name="return-value"></a>傳回值

對應於給定運行時庫錯誤值的枚舉值。

### <a name="remarks"></a>備註

有關可能的枚舉值的清單,請參閱[CFileException::m_cause。](#m_cause)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

## <a name="cfileexceptiongeterrormessage"></a><a name="geterrormessage"></a>檔案例外:抓取錯誤訊息

檢索描述異常的文本。

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>參數

*lpsz錯誤*<br/>
[進出]指向接收錯誤消息的緩衝區的指標。

*nMax錯誤*<br/>
[在]指定緩衝區可以保留的最大字元數。 這包括終止空字元。

*pnHelpContext*<br/>
[進出]指向接收説明上下文 ID 的無符號整數的指標。 如果`NULL`不返回 ID。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

如果指定的緩衝區太小,錯誤消息將被截斷。

### <a name="example"></a>範例

下列範例會使用 `CFileException::GetErrorMessage`。

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

## <a name="cfileexceptionm_cause"></a><a name="m_cause"></a>檔案例外::m_cause

包含 `CFileException` 列舉類型所定義的值。

```
int m_cause;
```

### <a name="remarks"></a>備註

此數據成員是**int**類型的公共變數。枚舉器及其含義如下:

- `CFileException::none`0: 未發生錯誤。

- `CFileException::genericException`1: 發生未指定的錯誤。

- `CFileException::fileNotFound`2: 找不到該檔。

- `CFileException::badPath`3: 全部或部分路徑無效。

- `CFileException::tooManyOpenFiles`4: 超過允許的打開檔數。

- `CFileException::accessDenied`5: 無法存取該檔。

- `CFileException::invalidFile`6: 有人嘗試使用無效的檔句柄。

- `CFileException::removeCurrentDir`7: 無法刪除目前工作目錄。

- `CFileException::directoryFull`8: 沒有更多的目錄條目。

- `CFileException::badSeek`9: 嘗試設定檔指標時出錯。

- `CFileException::hardIO`10: 存在硬體錯誤。

- `CFileException::sharingViolation`11: 分享。EXE 未載入,或者共用區域已鎖定。

- `CFileException::lockViolation`12: 有人試圖鎖定已鎖定的區域。

- `CFileException::diskFull`14: 磁碟已滿。

- `CFileException::endOfFile`15: 到達檔案結尾。

    > [!NOTE]
    >  這些 `CFileException` 原因列舉程式不同於 `CArchiveException` 原因列舉程式。

    > [!NOTE]
    > `CArchiveException::generic` 已被取代。 請改用 `genericException`。 如果在應用程式中使用**泛型**並且使用 /clr 構建,則生成的語法錯誤不容易被破譯。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

## <a name="cfileexceptionm_loserror"></a><a name="m_loserror"></a>檔案例外:m_lOsError

包含此異常的作業系統錯誤代碼。

```
LONG m_lOsError;
```

### <a name="remarks"></a>備註

有關錯誤代碼的清單,請參閱作業系統技術手冊。 此數據成員是 LONG 類型的公共變數。

## <a name="cfileexceptionm_strfilename"></a><a name="m_strfilename"></a>檔案例外:m_strFileName

包含此異常條件的檔名稱。

```
CString m_strFileName;
```

## <a name="cfileexceptionoserrortoexception"></a><a name="oserrortoexception"></a>檔案例外::錯誤例外

返回對應於給定*lOsError*值的枚舉器。 如果錯誤的未知,則函數會傳`CFileException::generic`回 。

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>參數

*LOsError*<br/>
特定於作業系統的錯誤代碼。

### <a name="return-value"></a>傳回值

對應於給定操作系統錯誤值的枚舉值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

## <a name="cfileexceptionthrowerrno"></a><a name="throwerrno"></a>檔例外::ThrowErrno

構造與給定`CFileException` *nErrno*值對應的物件,然後引發異常。

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>參數

*內埃爾諾*<br/>
運行時定義的整數錯誤代碼包括檔 ERRNO。H。

*lpszFile 名稱*<br/>
指向包含導致異常的檔名稱的檔名稱的字串的指標(如果可用)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

## <a name="cfileexceptionthrowoserror"></a><a name="throwoserror"></a>檔案例外::拋擲錯誤

引發`CFileException`與給定*lOsError*值對應的。 如果錯誤代碼未知,則函數將引發一個編碼為`CFileException::generic`的異常。

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>參數

*LOsError*<br/>
特定於作業系統的錯誤代碼。

*lpszFile 名稱*<br/>
指向包含導致異常的檔名稱的檔名稱的字串的指標(如果可用)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>另請參閱

[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[例外狀況處理](../../mfc/reference/exception-processing.md)
