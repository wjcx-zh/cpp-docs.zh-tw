---
title: CStdioFile 類別
ms.date: 08/29/2019
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
ms.openlocfilehash: 80ee65aa339a38b3d8434bc4c7cb977e263f037b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366005"
---
# <a name="cstdiofile-class"></a>CStdioFile 類別

表示運行時函數[fopen](../../c-runtime-library/reference/fopen-wfopen.md)打開的 C 執行時流檔。

## <a name="syntax"></a>語法

```
class CStdioFile : public CFile
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CStdio 檔案:CStdioFile](#cstdiofile)|從路徑或`CStdioFile`檔指標構造物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStdio 檔案:開啟](#open)|已多載。 打開設計用於與預設`CStdioFile`建構函數(覆蓋[檔::打開](../../mfc/reference/cfile-class.md#open))。|
|[CStdio 檔案:閱讀字串](#readstring)|讀取一行文本。|
|[CStdio 檔案:尋找](#seek)|定位當前檔指標。|
|[CStdio 檔:寫串](#writestring)|寫入一行文字。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CStdio檔:m_pStream](#m_pstream)|包含指向打開檔的指標。|

## <a name="remarks"></a>備註

流檔是緩衝的,可以在文本模式(預設)或二進位模式下打開。

文本模式為回車換行對提供特殊處理。 當您將行饋送(換行)字元 (0x0A) 寫入`CStdioFile`文本模式 物件時,位元組對(0x0D,0x0A)將發送到該檔。 讀取時,位元組對(0x0D,0x0A)將轉換為單個 0x0A 位元組。

[CFile](../../mfc/reference/cfile-class.md)函數[不支援](../../mfc/reference/cfile-class.md#duplicate)`CStdioFile`重複、[鎖定範圍](../../mfc/reference/cfile-class.md#lockrange)與[解鎖範圍](../../mfc/reference/cfile-class.md#unlockrange)。

如果在 上調用這些函`CStdioFile`數 ,您將獲得[CNot 支援異常](../../mfc/reference/cnotsupportedexception-class.md)。

`CStdioFile`有關使用的詳細資訊,請參閱[MFC](../../mfc/files-in-mfc.md)中的文章檔與*執行時庫參考*[中的檔案處理](../../c-runtime-library/file-handling.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="cstdiofilecstdiofile"></a><a name="cstdiofile"></a>CStdio 檔案:CStdioFile

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

*p 開放流*<br/>
指定呼叫 C 執行時函數[fopen](../../c-runtime-library/reference/fopen-wfopen.md)傳回的檔案指標。

*lpszFile 名稱*<br/>
指定作為所需檔的路徑的字串。 路徑可為相對路徑或絕對路徑。

*nOpenFlags*<br/>
指定檔案建立、檔案共享和檔案存取模式的選項。 可以使用位或 (**|**) 運算符指定多個選項。

需要一個文件訪問模式選項;其他模式是可選的。 有關模式選項和其他標誌的清單,請參閱[CFile:CFile。](../../mfc/reference/cfile-class.md#cfile) 在 MFC 版本 3.0 及更高版本中,允許共用標誌。

*pTM*<br/>
指向 CAtl 事務管理器物件的指標。

### <a name="remarks"></a>備註

預設構造函數不將檔附加到`CStdioFile`物件。 使用此建構函數時,`CStdioFile::Open`必須使用方法打開檔並將其附加`CStdioFile`到 物件。

單參數建構函數將打開的檔流附加到`CStdioFile`物件。 允許的指標值包括預定義的輸入/輸出檔指標*st丁**、stdout*或*stder。*

雙參數建構函數創建一個`CStdioFile`物件,並打開具有給定路徑的相應檔。

如果為*pOpenStream*或*lpszFileName*傳遞 NULL,則建構`CInvalidArgException*`函數會引發 。

如果無法開啟或建立檔案,則建構函數會引發`CFileException*`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

## <a name="cstdiofilem_pstream"></a><a name="m_pstream"></a>CStdio檔:m_pStream

數據`m_pStream`成員是 C 運行`fopen`時函數傳回的指向打開檔的指標。

```
FILE* m_pStream;
```

### <a name="remarks"></a>備註

如果文件從未打開或已關閉,則為 NULL。

## <a name="cstdiofileopen"></a><a name="open"></a>CStdio 檔案:開啟

已多載。 Open 設計用於`CStdioFile`預設建構函數。

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

*lpszFile 名稱*<br/>
是所需檔的路徑的字串。 路徑可為相對路徑或絕對路徑。

*nOpenFlags*<br/>
共用和訪問模式。 指定開啟檔時要執行的操作。 您可以使用位-OR(&#124;)運算符組合選項。 需要一個訪問許可權和一個共用選項;模式 創建和模式 No 繼承模式是可選的。

*pError*<br/>
指向將接收失敗操作狀態的現有文件異常物件的指標。

*pTM*<br/>
指向 `CAtlTransactionManager` 物件的指標。

### <a name="return-value"></a>傳回值

如果成功，則為 TRUE，否則為 FALSE。

### <a name="remarks"></a>備註

## <a name="cstdiofilereadstring"></a><a name="readstring"></a>CStdio 檔案:閱讀字串

從與`CStdioFile`物件關聯的檔中將文本數據讀取到緩衝區中,最多為*nMax*-1 個字元的限制。

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>參數

*lpsz*<br/>
指定指向使用者提供的緩衝區的指標,該緩衝區將接收 null 終止的文本字串。

*nMax*<br/>
指定要讀取的最大字元數,不包括終止空字元。

*rString*<br/>
對在`CString`函數返回時將包含字串的物件的引用。

### <a name="return-value"></a>傳回值

指向包含文本數據的緩衝區的指標。 如果未讀取任何數據就到達了文件結尾;或者,如果未讀取任何數據就達到檔結尾,則 FALSE。

### <a name="remarks"></a>備註

讀取由第一個領線字元停止。 在這種情況下,如果讀取的字元少於*nMax*-1 字元,則緩衝區中存儲了換行元。 在這兩種情況下都附加了空字元 ("\0")。

[CFile::讀取](../../mfc/reference/cfile-class.md#read)也可用於文本模式輸入,但它不會在回車返回行饋送對上終止。

> [!NOTE]
> 此`CString`函數的版本將`'\n'`刪除 "如果存在";如果LPTSTR 版本不。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

## <a name="cstdiofileseek"></a><a name="seek"></a>CStdio 檔案:尋找

在以前打開的檔中重新定位指標。

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>參數

*LOff*<br/>
要移動指標的位元組數。

*n 從*<br/>
指標移動模式。 必須為下列其中一個值：

- `CFile::begin`:從文件的開頭向前移動檔指標*lOff*位元組。

- `CFile::current`:從檔案中的當前位置移動檔指標*lOff*位元組。

- `CFile::end`:從文件末尾移動檔指標*lOff*位元組。 請注意 *,lOff*必須是負的才能查找到現有檔中;正值將查找檔末尾。

### <a name="return-value"></a>傳回值

如果請求的位置是合法的,則`Seek`從文件開頭返回新的位元組偏移量。 否則,返回值將未定義,並引發`CFileException`物件。

### <a name="remarks"></a>備註

該`Seek`函數允許通過絕對或相對地將指標移動指定數量來隨機存取檔的內容。 在查找過程中實際上不會讀取任何數據。 如果請求的位置大於檔的大小,檔長度將擴展到該位置,並且不會引發任何異常。

打開檔時,檔指標定位在偏移量 0,即檔的開頭。

此`Seek`執行時庫 (CRT) 函`fseek`數 。 在文本模式下打開的`Seek`流上的用法有幾個限制。 有關詳細資訊,請參閱[fseek,_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)。

### <a name="example"></a>範例

下面的範例展示如何使用`Seek``cfile`從文件開頭移動指標 1000 位元組。 請注意,`Seek`不讀取資料,因此您隨後必須調用[CStdioFile::ReadString](#readstring)讀取資料。

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

## <a name="cstdiofilewritestring"></a><a name="writestring"></a>CStdio 檔:寫串

將數據從緩衝區寫入與`CStdioFile`對象關聯的檔。

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>參數

*lpsz*<br/>
指定指向包含 null 終止字串的緩衝區的指標。

### <a name="remarks"></a>備註

取消 null`\0`字元 ( ) 不會寫入檔案。 此方法將*lpsz*中的換行符寫入檔,作為回車換行對。

如果要將未為檔案終止的數據寫入檔,請使用`CStdioFile::Write`或[CFile:::write。](../../mfc/reference/cfile-class.md#write)

如果為`CInvalidArgException*`*lpsz*參數指定 NULL,則此方法將引發 。

此方法引發`CFileException*`以回應檔系統錯誤。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>另請參閱

[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[檔案::D](../../mfc/reference/cfile-class.md#duplicate)<br/>
[檔案檔案:鎖定範圍](../../mfc/reference/cfile-class.md#lockrange)<br/>
[檔案檔案:解鎖範圍](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[CNotSupportedException 類別](../../mfc/reference/cnotsupportedexception-class.md)
