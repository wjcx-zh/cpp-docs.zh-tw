---
title: CStdioFile 類別
ms.date: 11/04/2016
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
helpviewer_keywords:
- CStdioFile [MFC], CStdioFile
- CStdioFile [MFC], Open
- CStdioFile [MFC], ReadString
- CStdioFile [MFC], Seek
- CStdioFile [MFC], WriteString
- CStdioFile [MFC], m_pStream
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
ms.openlocfilehash: 068e59fdc19821487bc78141d10743363221518e
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375842"
---
# <a name="cstdiofile-class"></a>CStdioFile 類別

表示由執行時間函式[fopen](../../c-runtime-library/reference/fopen-wfopen.md)所開啟的 C 執行時間資料流程檔案。

## <a name="syntax"></a>語法

```
class CStdioFile : public CFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|從路徑或檔案指標來構造物件。`CStdioFile`|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStdioFile::Open](#open)|多載。 Open 的設計目的是要與預設`CStdioFile`的處理常式搭配使用 (覆寫[CFile:: Open](../../mfc/reference/cfile-class.md#open))。|
|[CStdioFile::ReadString](#readstring)|讀取一行文字。|
|[CStdioFile::Seek](#seek)|放置目前的檔案指標。|
|[CStdioFile::WriteString](#writestring)|寫入一行文字。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|包含開啟檔案的指標。|

## <a name="remarks"></a>備註

串流檔案會經過緩衝處理, 而且可以在文字模式 (預設) 或二進位模式中開啟。

文字模式會提供對換行回車的特殊處理。 當您將換行字元 (分行符號) 寫入文字模式`CStdioFile`物件時, 會將位元組配對 (0x0D、0x0A) 傳送至檔案。 當您讀取時, 位元組配對 (0x0D, 0x0A) 會轉譯為單一0x0A 位元組。

[不支援](../../mfc/reference/cfile-class.md#duplicate) [CFile 函數](../../mfc/reference/cfile-class.md)重複、 [LockRange](../../mfc/reference/cfile-class.md#lockrange)和[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) 。 `CStdioFile`

如果您在上`CStdioFile`呼叫這些函式, 您會收到[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

如需`CStdioFile`有關使用的詳細資訊, 請參閱《*執行時間程式庫參考*》中的文章 MFC 和檔案[處理](../../c-runtime-library/file-handling.md)中的[檔](../../mfc/files-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="cstdiofile"></a>CStdioFile:: CStdioFile

建構並初始化 `CStdioFile` 物件。

```
CStdioFile();
CStdioFile(CAtlTransactionManager* pTM);
  CStdioFile(FILE* pOpenStream);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>參數

*pOpenStream*<br/>
指定呼叫 C 執行時間函數[fopen](../../c-runtime-library/reference/fopen-wfopen.md)所傳回的檔案指標。

*lpszFileName*<br/>
指定字串, 這是所需檔案的路徑。 路徑可以是相對或絕對。

*nOpenFlags*<br/>
指定檔案建立、檔案共用和檔案存取模式的選項。 您可以使用位 or ( **|** ) 運算子來指定多個選項。

需要一個檔案存取模式選項;其他模式則是選擇性的。 如需模式選項和其他旗標的清單, 請參閱[CFile:: CFile](../../mfc/reference/cfile-class.md#cfile) 。 在 MFC 版本3.0 和更新版本中, 允許共用旗標。

*pTM*<br/>
CAtlTransactionManager 物件的指標。

### <a name="remarks"></a>備註

預設的構造函式不會將檔案附加`CStdioFile`至物件。 使用此函數時, 您必須使用`CStdioFile::Open`方法來開啟檔案, 並將它附加`CStdioFile`至物件。

單一參數的構造函式會將開啟的檔案資料流程`CStdioFile`附加至物件。 允許的指標值包含預先定義的輸入/輸出檔案指標*stdin*、 *stdout*或*stderr*。

雙參數的函式會建立`CStdioFile`物件, 並以指定的路徑開啟對應的檔案。

如果您為*pOpenStream*或*lpszFileName*傳遞 Null, 則此`CInvalidArgException*`方法會擲回。

如果無法開啟或建立檔案, 則此`CFileException*`函式會擲回。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

##  <a name="m_pstream"></a>CStdioFile:: m_pStream

資料成員是 C 運行`fopen`時間函式所傳回之開啟檔案的指標。 `m_pStream`

```
FILE* m_pStream;
```

### <a name="remarks"></a>備註

如果檔案從未開啟或已關閉, 則為 Null。

##  <a name="open"></a>CStdioFile:: Open

多載。 Open 的設計目的是要與預設`CStdioFile`的處理常式搭配使用。

```
virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>參數

*lpszFileName*<br/>
字串, 這是所需檔案的路徑。 路徑可以是相對或絕對。

*nOpenFlags*<br/>
共用和存取模式。 指定開啟檔案時要採取的動作。 您可以使用位 OR (&#124;) 運算子來結合選項。 需要一個存取權限和一個共用選項;modeCreate 和 modeNoInherit 模式是選擇性的。

*pError*<br/>
現有檔案例外狀況物件的指標, 會接收失敗作業的狀態。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

##  <a name="readstring"></a>CStdioFile:: ReadString

從與`CStdioFile`物件相關聯的檔案中, 將文字資料讀入緩衝區中, 最多可達*n 上限*-1 個字元的限制。

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>參數

*lpsz*<br/>
指定使用者提供之緩衝區的指標, 此緩衝區將會接收以 null 結束的文字字串。

*nMax*<br/>
指定要讀取的最大字元數, 而不是計算終止的 null 字元。

*rString*<br/>
當函式傳回`CString`時, 將包含字串之物件的參考。

### <a name="return-value"></a>傳回值

包含文字資料的緩衝區指標。 如果已到達檔案結尾, 但未讀取任何資料, 則為 Null。如果為布林值, 則為 FALSE, 如果已到達檔案結尾, 則不讀取任何資料。

### <a name="remarks"></a>備註

讀取是由第一個分行符號所停止。 如果在此情況下, 已讀取少於*n 上限*-1 個字元, 則分行符號會儲存在緩衝區中。 在任一情況下, 都會附加 null 字元 (' \ 0 ')。

[CFile:: Read](../../mfc/reference/cfile-class.md#read)也適用于文字模式輸入, 但它不會在換行的傳回分行符號上終止。

> [!NOTE]
>  此`CString`函式的版本會`'\n'`移除 (如果有的話), 而 LPTSTR 版本則不會。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

##  <a name="seek"></a>CStdioFile:: Seek

重新置放先前開啟之檔案中的指標。

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>參數

*lOff*<br/>
要移動指標的位元組數目。

*nFrom*<br/>
指標移動模式。 必須是下列其中一個值:

- `CFile::begin`：將檔案指標*lOff*位元組從檔案的開頭往前移動。

- `CFile::current`：從檔案中的目前位置移動檔案指標*lOff*位元組。

- `CFile::end`：將檔案指標*lOff* bytes 從檔案結尾移動。 請注意, *lOff*必須為負數, 才能搜尋現有的檔案。正數值會搜尋超過檔案結尾。

### <a name="return-value"></a>傳回值

如果要求的位置是合法的`Seek` , 則會從檔案的開頭傳回新的位元組位移。 否則, 傳回值會是未定義的`CFileException` , 而且會擲回物件。

### <a name="remarks"></a>備註

`Seek`函式會將指標移到指定的數量 (絕對或相對), 以允許隨機存取檔案的內容。 搜尋期間不會實際讀取任何資料。 如果要求的位置大於檔案的大小, 檔案長度將會延伸至該位置, 而且不會擲回任何例外狀況。

當檔案開啟時, 檔案指標會放在檔案開頭的位移0。

這個的`Seek`執行是以執行時間程式庫 (CRT) 函數`fseek`為基礎。 在以文字模式開啟的資料流程`Seek`上使用時, 有幾項限制。 如需詳細資訊, 請參閱[fseek、_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)。

### <a name="example"></a>範例

下列範例顯示如何使用`Seek` , 將指標1000位元組從檔案的開頭`cfile`移動。 請注意, 不會讀取資料,因此您之後必須呼叫CStdioFile::ReadString來讀取資料。`Seek` [](#readstring)

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

##  <a name="writestring"></a>CStdioFile:: WriteString

將資料從緩衝區寫入與`CStdioFile`物件相關聯的檔案。

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>參數

*lpsz*<br/>
指定包含以 null 終止之字串的緩衝區指標。

### <a name="remarks"></a>備註

終止的 null 字元 ( `\0`) 不會寫入檔案。 這個方法會將*lpsz*中的分行符號寫入檔案, 做為一組換行字元。

如果您想要將不是以 null 終止的資料寫入檔案, 請使用`CStdioFile::Write`或[CFile:: write](../../mfc/reference/cfile-class.md#write)。

`CInvalidArgException*`如果您對*lpsz*參數指定 Null, 這個方法會擲回。

這個方法`CFileException*`會擲回, 以回應檔案系統錯誤。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>另請參閱

[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[CNotSupportedException 類別](../../mfc/reference/cnotsupportedexception-class.md)
