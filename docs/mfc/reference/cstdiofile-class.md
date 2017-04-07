---
title: "Cgopherfile 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
dev_langs:
- C++
helpviewer_keywords:
- CStdioFile class
- I/O [MFC], stream
- stream I/O
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: f3f036b409067676fdf12db9751cac1ea8025140
ms.lasthandoff: 02/24/2017

---
# <a name="cstdiofile-class"></a>Cgopherfile 類別
表示執行階段函式所開啟的 C 執行階段資料流檔案[fopen](../../c-runtime-library/reference/fopen-wfopen.md)。  
  
## <a name="syntax"></a>語法  
  
```  
class CStdioFile : public CFile  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CStdioFile::CStdioFile](#cstdiofile)|建構`CStdioFile`物件的路徑或檔案的指標。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CStdioFile::Open](#open)|多載。 開啟已設計為搭配預設`CStdioFile`建構函式 (覆寫[CFile::Open](../../mfc/reference/cfile-class.md#open))。|  
|[CStdioFile::ReadString](#readstring)|讀取一行文字。|  
|[CStdioFile::Seek](#seek)|將目前的檔案指標。|  
|[CStdioFile::WriteString](#writestring)|寫入一行文字。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CStdioFile::m_pStream](#m_pstream)|包含在開啟檔案的指標。|  
  
## <a name="remarks"></a>備註  
 資料流檔案會進行緩衝處理，並且可以在文字模式 （預設值） 或二進位模式中開啟。  
  
 文字模式提供歸位換成對特殊處理。 當您撰寫一個新行字元 (0x0A) 以文字模式`CStdioFile`物件時，位元組組 (0x0D，0x0A) 傳送到檔案。 當您閱讀，位元組組 (0x0D，0x0A) 轉譯成單一的 0x0A 位元組。  
  
 [CFile](../../mfc/reference/cfile-class.md)函式[重複](../../mfc/reference/cfile-class.md#duplicate)， [LockRange](../../mfc/reference/cfile-class.md#lockrange)，和[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)不支援`CStdioFile`。  
  
 如果您呼叫這些函式上`CStdioFile`，就會[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 如需有關使用`CStdioFile`，請參閱文章[MFC 中的檔案](../../mfc/files-in-mfc.md)和[檔案處理](../../c-runtime-library/file-handling.md)中*執行階段程式庫參考*。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CStdioFile`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="cstdiofile"></a>CStdioFile::CStdioFile  
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
 `pOpenStream`  
 指定 C 執行階段函式的呼叫所傳回的檔案指標[fopen](../../c-runtime-library/reference/fopen-wfopen.md)。  
  
 `lpszFileName`  
 指定所需的檔案路徑的字串。 路徑可以是相對或絕對。  
  
 `nOpenFlags`  
 指定用來建立檔案、 檔案共用與檔案存取模式選項。 您可以指定多個選項使用的位元 OR ( `|`) 運算子。  
  
 其中一個檔案存取模式選項是必要的。其他模式是選擇性的。 請參閱[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)模式選項和其他旗標的清單。 在 MFC 3.0 版和更新版本中，允許共用旗標。  
  
 `pTM`  
 CAtlTransactionManager 物件的指標。  
  
### <a name="remarks"></a>備註  
 預設建構函式不會附加至檔案`CStdioFile`物件。 當使用這個建構函式，您必須使用`CStdioFile::Open`方法，以開啟檔案，並將其附加至`CStdioFile`物件。  
  
 單一參數的建構函式會將附加至開啟的檔案資料流`CStdioFile`物件。 允許包括預先定義的輸入/輸出檔案指標的指標值`stdin`， `stdout`，或`stderr`。  
  
 兩個參數的建構函式建立`CStdioFile`物件，並使用指定的路徑開啟對應的檔案。  
  
 如果您傳遞`NULL`針對`pOpenStream`或`lpszFileName`，建構函式會擲回`CInvalidArgException*`。  
  
 如果無法開啟或建立檔案，建構函式會擲回`CFileException*`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&37;](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]  
  
##  <a name="m_pstream"></a>CStdioFile::m_pStream  
 `m_pStream`資料成員是開啟的檔案的指標，C 執行階段函式所傳回`fopen`。  
  
```  
FILE* m_pStream;  
```  
  
### <a name="remarks"></a>備註  
 它是**NULL**如果從未開啟檔案，或已關閉。  
  
##  <a name="open"></a>CStdioFile::Open  
 多載。 開啟已設計為搭配預設`CStdioFile`建構函式。  
  
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
 `lpszFileName`  
 所需的檔案的路徑字串。 路徑可以是相對或絕對。  
  
 `nOpenFlags`  
 共用和存取模式。 指定當開啟檔案時要採取的動作。 您可以使用位元 OR (|) 運算子來合併選項。 一個存取權，以及一個共用選項是必要的。modeCreate 和 modeNoInherit 模式是選擇性的。  
  
 `pError`  
 現有的檔案例外狀況物件，將會收到失敗作業的狀態指標。  
  
 `pTM`  
 指向 `CAtlTransactionManager` 物件的指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功，則為 `TRUE`，否則為 `FALSE`。  
  
### <a name="remarks"></a>備註  
  
##  <a name="readstring"></a>CStdioFile::ReadString  
 文字資料讀取至緩衝區，上限是`nMax`相關聯的檔案從-1 字元`CStdioFile`物件。  
  
```  
virtual LPTSTR ReadString(
    LPTSTR lpsz,  
    UINT nMax);  
  
virtual BOOL ReadString(CString& rString);
```  
  
### <a name="parameters"></a>參數  
 `lpsz`  
 指定的使用者提供的緩衝區，將會收到 null 結尾的文字字串的指標。  
  
 `nMax`  
 指定要讀取的字元數目上限不計結束的 null 字元。  
  
 `rString`  
 參考`CString`函式傳回時，將包含字串的物件。  
  
### <a name="return-value"></a>傳回值  
 包含文字資料緩衝區的指標。 **NULL**或檔案結尾已到達未讀取任何資料; 如果布林值，如果**FALSE**如果檔案結尾已到達未讀取任何資料。  
  
### <a name="remarks"></a>備註  
 讀取已停止的第一個新行字元。 如果在此情況下，少於`nMax`已經讀取-1 字元、 新行字元會儲存在緩衝區。 在任一情況下，會附加 null 字元 ('\0')。  
  
 [CFile::Read](../../mfc/reference/cfile-class.md#read)時也可以使用文字模式的輸入，但它不會終止歸位換組。  
  
> [!NOTE]
>  `CString`移除此函式版本`'\n'`存在; 如果`LPTSTR`版本並不會。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&38;](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]  
  
##  <a name="seek"></a>CStdioFile::Seek  
 指標重新置放在先前開啟的檔案。  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOff,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>參數  
 `lOff`  
 移動指標的位元組數目。  
  
 `nFrom`  
 指標移動模式。 必須是下列值之一︰  
  
- `CFile::begin`︰ 移動檔案指標`lOff`轉寄從檔案開頭的位元組。  
  
- `CFile::current`︰ 移動檔案指標`lOff`位元組從目前位置的檔案中。  
  
- `CFile::end`︰ 移動檔案指標`lOff`從檔案結尾的位元組。 請注意，`lOff`必須是要搜尋到現有的負檔案; 正值將會搜尋超出檔案結尾。  
  
### <a name="return-value"></a>傳回值  
 如果要求的位置是合法的`Seek`傳回新的位元組位移，從檔案的開頭。 否則，傳回的值會是未定義和`CFileException`物件就會擲回。  
  
### <a name="remarks"></a>備註  
 `Seek`函式允許隨機存取檔案的內容移動指標指定的數量，具有絕對或相對。 在搜尋期間實際不讀取任何資料。 如果要求的位置超過檔案的大小，檔案的長度會擴充至該位置，並將擲回任何例外狀況。  
  
 開啟檔案時，檔案指標位於位移 0，檔案的開頭。  
  
 這項實作的`Seek`根據執行階段程式庫 (CRT) 函式`fseek`。 使用方式有數個限制`Seek`文字模式開啟的資料流。 如需詳細資訊，請參閱[fseek、 _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用`Seek`移動指標 1000 個位元組從開頭`cfile`檔案。 請注意，`Seek`不會讀取資料，因此您接下來必須呼叫[CStdioFile::ReadString](#readstring)讀取資料。  
  
 [!code-cpp[NVC_MFCFiles #&39;](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]  
  
##  <a name="writestring"></a>CStdioFile::WriteString  
 緩衝區中的資料寫入至相關聯的檔案`CStdioFile`物件。  
  
```  
virtual void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>參數  
 `lpsz`  
 指定包含以 null 終止字串緩衝區的指標。  
  
### <a name="remarks"></a>備註  
 結束的 null 字元 ( `\0`) 不會寫入至檔案。 這個方法會寫入新行字元`lpsz`歸位字元/換行對此檔案。  
  
 如果您想要寫入的資料，不是以 null 結束的檔案時，使用`CStdioFile::Write`或[CFile::Write](../../mfc/reference/cfile-class.md#write)。  
  
 這個方法會擲回`CInvalidArgException*`如果您指定`NULL`的`lpsz`參數。  
  
 這個方法會擲回`CFileException*`回應檔案系統錯誤。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCFiles #&40;](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CFile 類別](../../mfc/reference/cfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFile 類別](../../mfc/reference/cfile-class.md)   
 [CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)   
 [CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)   
 [CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)   
 [CNotSupportedException 類別](../../mfc/reference/cnotsupportedexception-class.md)

