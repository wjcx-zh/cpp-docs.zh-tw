---
title: 例外狀況處理
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], exception handling
- DAO (Data Access Objects), exceptions [MFC]
- OLE exceptions [MFC], MFC functions
- exceptions [MFC], processing
- exception macros [MFC]
- termination functions, MFC
- MFC, exceptions
- exceptions [MFC], MFC throwing functions
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
ms.openlocfilehash: d819c170f47ea259e776bce6db0a6971e3f54bec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365720"
---
# <a name="exception-processing"></a>例外狀況處理

當程式執行時,可能會出現許多稱為"異常"的異常條件和錯誤。 這些可能包括記憶體不足、資源分配錯誤和找不到檔。

Microsoft 基礎類庫使用一種異常處理方案,該方案與 ANSI 標準委員會提出的 C++方案緊密建模。 在調用可能遇到異常情況的函數之前,必須設置異常處理程式。 如果函數遇到異常情況,它將引發異常,並將控件傳遞給異常處理程式。

Microsoft 基礎類庫中包含的幾個宏將設置異常處理程式。 許多其他全域函數有助於引發專用異常並在必要時終止程式。 這些宏和全域函數分為以下幾類:

- 異常宏,它構造異常處理程式。

- 異常引發函數),生成特定類型的異常。

- 終止函數,導致程序終止。

有關範例和更多詳細資訊,請參閱文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="exception-macros"></a>異常宏

|||
|-|-|
|[土耳其里拉](#try)|指定用於異常處理的代碼塊。|
|[抓住](#catch)|指定一個程式碼塊,用於從前面的**TRY**塊捕獲異常。|
|[CATCH_ALL](#catch_all)|指定一個程式碼塊,用於捕獲前面**TRY**塊中的所有異常。|
|[AND_CATCH](#and_catch)|指定一個程式碼塊,用於從前面的**TRY**塊捕捉其他異常類型。|
|[AND_CATCH_ALL](#and_catch_all)|指定一個程式碼塊,用於捕獲前面**TRY**塊中引發的任何其他異常類型。|
|[END_CATCH](#end_catch)|結束最後一個**CATCH**或**AND_CATCH**代碼塊。|
|[END_CATCH_ALL](#end_catch_all)|結束最後**一個CATCH_ALL**代碼塊。|
|[扔](#throw)|引發指定的異常。|
|[THROW_LAST](#throw_last)|將當前處理的異常引發到下一個外部處理程式。|

### <a name="exception-throwing-functions"></a>例外引發函數

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|引發存檔異常。|
|[AfxThrowFileException](#afxthrowfileexception)|引發文件異常。|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|引發無效參數異常。|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|引發記憶體異常。|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|引發不支持的異常。|
|[AfxThrowResourceException](#afxthrowresourceexception)|引發未找到的 Windows 資源異常。|
|[AfxThrowUserException](#afxthrowuserexception)|在用戶啟動的程式操作中引發異常。|

MFC 提供兩個專門針對 OLE 異常的異常引發功能:

### <a name="ole-exception-functions"></a>OLE 例外函數

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|在 OLE 自動化功能中引發異常。|
|[AfxThrowOleException](#afxthrowoleexception)|引發 OLE 異常。|

為了支援資料庫異常,資料庫類提供了兩個異常類和`CDBException``CDaoException`和全域函數來支援異常類型:

### <a name="dao-exception-functions"></a>DAO 例外函數

|||
|-|-|
|[阿不都·阿不都拉多例外](#afxthrowdaoexception)|從您自己的代碼中拋出一個[CDaoException。](../../mfc/reference/cdaoexception-class.md)|
|[AfxThrowDBException](#afxthrowdbexception)|從您自己的代碼中引發[CDBException。](../../mfc/reference/cdbexception-class.md)|

MFC 提供以下終止功能:

### <a name="termination-functions"></a>終止功能

|||
|-|-|
|[AfxAbort](#afxabort)|調用以在發生致命錯誤時終止應用程式。|

## <a name="try"></a><a name="try"></a>嘗試

設置**TRY**塊。

```
TRY
```

### <a name="remarks"></a>備註

**TRY**塊標識可能會引發異常的代碼塊。 這些異常在以下**CATCH**和**AND_CATCH**塊中處理。 允許遞歸:異常可以通過忽略它們或使用THROW_LAST宏傳遞給外部**TRY**塊。 使用END_CATCH或END_CATCH_ALL宏結束**TRY**塊。

有關詳細資訊,請參閱文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="example"></a>範例

請參閱[CATCH](#catch)的範例。

### <a name="requirements"></a>需求

標頭：afx.h

## <a name="catch"></a><a name="catch"></a>抓住

定義捕獲前面**TRY**塊中引發的第一個異常類型的代碼塊。

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_class*<br/>
指定要測試的異常類型。 有關標準異常類的清單,請參閱類[Cexception](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
指定將由巨集建立的例外狀況物件指標的名稱。 可以使用指標名稱訪問**CATCH**塊中的異常物件。 會為您宣告這個變數。

### <a name="remarks"></a>備註

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 調用THROW_LAST宏以將處理轉移到下一個外部異常幀。 使用END_CATCH宏結束**TRY**塊。

如果*exception_class*`CException`是類 ,則將捕獲所有異常類型。 您可以使用[CObject:IsKindOf](../../mfc/reference/cobject-class.md#iskindof)成員函數來確定引發的特定異常。 捕獲多種異常的更好方法是使用順序**AND_CATCH**語句,每種語句都具有不同的異常類型。

異常物件指標由宏創建。 你不需要自己聲明它。

> [!NOTE]
> **CATCH**塊定義為由大括弧劃定的C++作用域。 如果您在這個範圍中宣告變數，變數就只能在該範圍內存取。 這也適用於*exception_object_pointer_name。*

有關異常和 CATCH 宏的詳細資訊,請參閱文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

## <a name="catch_all"></a><a name="catch_all"></a>CATCH_ALL

定義捕獲前面**TRY**塊中引發的所有異常類型的代碼塊。

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_object_pointer_name*<br/>
指定將由巨集建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取在 `CATCH_ALL` 區塊中的例外狀況物件。 會為您宣告這個變數。

### <a name="remarks"></a>備註

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 叫用 `THROW_LAST` 巨集將處理移位到下個外部例外狀況框架。 如果使用**CATCH_ALL**,請用END_CATCH_ALL宏結束**TRY**塊。

> [!NOTE]
> **CATCH_ALL**塊定義為由大括弧劃定的C++作用域。 如果您在這個範圍中宣告變數，變數就只能在該範圍內存取。

有關異常的詳細資訊,請參閱文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="example"></a>範例

請參閱[CFile 的範例::中止](../../mfc/reference/cfile-class.md#abort)。

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="and_catch"></a><a name="and_catch"></a>AND_CATCH

定義代碼塊,用於捕獲在前面的**TRY**塊中引發的其他異常類型。

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_class*<br/>
指定要測試的異常類型。 有關標準異常類的清單,請參閱類[Cexception](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
由宏創建的異常物件指標的名稱。 可以使用指標名稱訪問**AND_CATCH**塊中的異常物件。 會為您宣告這個變數。

### <a name="remarks"></a>備註

使用 CATCH 宏捕獲一種異常類型,然後AND_CATCH宏捕獲每個後續類型。 使用END_CATCH宏結束**TRY**塊。

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 調用**AND_CATCH**塊中的THROW_LAST宏,將處理轉移到下一個外部異常幀。 **AND_CATCH**標記前一個**CATCH**或**AND_CATCH**塊的末尾。

> [!NOTE]
> **AND_CATCH**塊定義為C++範圍(由大括弧定義)。 如果在此作用域中聲明變數,請記住它們只能在該作用域內訪問。 這也適用於*exception_object_pointer_name*變數。

### <a name="example"></a>範例

請參閱[CATCH](#catch)的範例。

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="and_catch_all"></a><a name="and_catch_all"></a>AND_CATCH_ALL

定義代碼塊,用於捕獲在前面的**TRY**塊中引發的其他異常類型。

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_object_pointer_name*<br/>
由宏創建的異常物件指標的名稱。 可以使用指標名稱訪問**AND_CATCH_ALL**塊中的異常物件。 會為您宣告這個變數。

### <a name="remarks"></a>備註

使用**CATCH**宏捕獲一種異常類型,然後AND_CATCH_ALL宏捕獲所有其他後續類型。 如果使用AND_CATCH_ALL,請用END_CATCH_ALL宏結束**TRY**塊。

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 調用**AND_CATCH_ALL**塊中的THROW_LAST宏以將處理轉移到下一個外部異常幀。 **AND_CATCH_ALL**標記前一個**CATCH**或**AND_CATCH_ALL**塊的末尾。

> [!NOTE]
> **AND_CATCH_ALL**塊定義為C++範圍(由大括弧定義)。 如果在此作用域中聲明變數,請記住它們只能在該作用域內訪問。

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="end_catch"></a><a name="end_catch"></a>END_CATCH

標記最後一個**CATCH**或**AND_CATCH**塊的末尾。

```
END_CATCH
```

### <a name="remarks"></a>備註

有關END_CATCH宏的詳細資訊,請參閱文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="end_catch_all"></a><a name="end_catch_all"></a>END_CATCH_ALL

標記最後一**個CATCH_ALL88**或**AND_CATCH_ALL**塊的結束。

```
END_CATCH_ALL
```

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="throw-mfc"></a><a name="throw"></a>THROW (MFC)

引發指定的異常。

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>參數

*exception_object_pointer*<br/>
指向派生自`CException`的異常物件。

### <a name="remarks"></a>備註

**THROW**中斷程式執行,將控制權傳遞到程式中的關聯**CATCH**塊。 如果尚未提供**CATCH**塊,則控制項將傳遞給 Microsoft 基礎類庫模組,該模組列印錯誤訊息並退出。

有關詳細資訊,請參閱文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="throw_last"></a><a name="throw_last"></a>THROW_LAST

將異常扔回下一個外部**CATCH**塊。

```
THROW_LAST()
```

### <a name="remarks"></a>備註

此宏允許您引發本地創建的異常。 如果您嘗試引發剛剛捕獲的異常,它通常會超出範圍並被刪除。 對於**THROW_LAST**,異常將正確傳遞給下一個**CATCH**處理程式。

有關詳細資訊,請參閱文章["例外](../../mfc/exception-handling-in-mfc.md)"。

### <a name="example"></a>範例

請參閱[CFile 的範例::中止](../../mfc/reference/cfile-class.md#abort)。

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="afxthrowarchiveexception"></a><a name="afxthrowarchiveexception"></a>AfxThrow存檔例外

引發存檔異常。

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>參數

*cause*<br/>
指定指示異常原因的整數。 有關可能值的清單,請參閱[CArchiveException:::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause)。

*lpsz 壓縮檔名稱*<br/>
指向包含導致異常`CArchive`的物件的名稱的字串(如果可用)。

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="afxthrowfileexception"></a><a name="afxthrowfileexception"></a>AfxThrow檔例外

引發文件異常。

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>參數

*cause*<br/>
指定指示異常原因的整數。 有關可能值的清單,請參閱[CFileException:::m_cause](../../mfc/reference/cfileexception-class.md#m_cause)。

*LOsError*<br/>
包含說明異常原因的操作系統錯誤編號(如果可用)。 有關錯誤代碼的清單,請參閱作業系統手冊。

*lpszFile 名稱*<br/>
指向包含導致異常的檔案名稱的檔名稱的字串(如果可用)。

### <a name="remarks"></a>備註

您負責根據作業系統錯誤代碼確定原因。

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="afxthrowinvalidargexception"></a><a name="afxthrowinvalidargexception"></a>AfxThrow 無效異常

引發無效參數異常。

### <a name="syntax"></a>語法

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>備註

使用無效參數時調用此函數。

### <a name="requirements"></a>需求

**標題:** afx.h

## <a name="afxthrowmemoryexception"></a><a name="afxthrowmemoryexception"></a>AfxThrow 記憶異常

引發記憶體異常。

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>備註

如果對基礎系統記憶體分配器(如**malloc**和[GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows 函數)的調用失敗,請調用此功能。 您無需呼叫它**作為新**,因為如果記憶體分配失敗 **,new**將自動引發記憶體異常。

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="afxthrownotsupportedexception"></a><a name="afxthrownotsupportedexception"></a>AfxThrow 不支援例外

引發由請求不支援的功能的結果的異常。

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="afxthrowresourceexception"></a><a name="afxthrowresourceexception"></a>AfxThrow 資源異常

引發資源異常。

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>備註

當無法載入 Windows 資源時,通常會調用此功能。

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="afxthrowuserexception"></a><a name="afxthrowuserexception"></a>AfxThrowUser 例外

引發異常以停止最終使用者操作。

```
void AfxThrowUserException();
```

### <a name="remarks"></a>備註

通常在向使用者報告錯誤後立即`AfxMessageBox`呼叫此功能。

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="afxthrowoledispatchexception"></a><a name="afxthrowoledispatchexception"></a>AfxThrowOle調度異常

使用此函式在 OLE Automation 函式內擲回例外狀況。

```
void AFXAPI AfxThrowOleDispatchException(
    WORD wCode ,
    LPCSTR lpszDescription,
    UINT nHelpID = 0);

void AFXAPI AfxThrowOleDispatchException(
    WORD wCode,
    UINT nDescriptionID,
    UINT nHelpID = -1);
```

### <a name="parameters"></a>參數

*w代碼*<br/>
應用程式特定的錯誤碼。

*lpsz描述*<br/>
錯誤的詳細描述。

*描述 ID*<br/>
詳細錯誤描述的資源 ID。

*nHelpID*<br/>
您的應用程式說明 (.HLP) 檔的說明內容。

### <a name="remarks"></a>備註

提供給此函式的資訊可以透過驅動應用程式 (Microsoft Visual Basic 或其他 OLE Automation 用戶端應用程式) 來加以顯示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="afxthrowoleexception"></a><a name="afxthrowoleexception"></a>阿不都·阿不都列索

創建類型`COleException`物件並引發異常。

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>參數

*Sc*<br/>
指示異常原因的 OLE 狀態代碼。

*人力資源*<br/>
處理指示異常原因的結果代碼。

### <a name="remarks"></a>備註

將 HRESULT 作為參數的版本將結果代碼轉換為相應的 SCODE。 有關 HRESULT 與 SCODE 的詳細資訊,請參閱 Windows SDK 中的[COM 錯誤代碼結構](/windows/win32/com/structure-of-com-error-codes)。

### <a name="requirements"></a>需求

  **標題**afxdao.h

## <a name="afxthrowdaoexception"></a><a name="afxthrowdaoexception"></a>阿fxThrowDao例外

呼叫此函數從您自己的代碼中引發[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的異常。

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>參數

*nAfxDao錯誤*<br/>
表示 DAO 擴展錯誤代碼的整數值,可以是[CDaoException:::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)下列出的值之一。

*scode*<br/>
來自 DAO 的 OLE 錯誤代碼,類型為 SCODE。 有關詳細資訊,請參閱[CDaoexception::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode)。

### <a name="remarks"></a>備註

框架也稱為`AfxThrowDaoException`。 在呼叫中,您可以傳遞其中一個參數或兩者。 例如,如果要引發**CDaoException::nAfxDaoError**中定義的錯誤之一,但您不關心*scode*參數,請透過*nAfxDaoError*參數中的有效代碼,並接受*scode*的預設值。

有關與 MFC DAO 類相關的異常的資訊,`CDaoException`請參閱本書 中的類和文章[「例外:資料庫例外](../../mfc/exceptions-database-exceptions.md)」。

### <a name="requirements"></a>需求

  **頭**afxdb.h

## <a name="afxthrowdbexception"></a><a name="afxthrowdbexception"></a>AfxThrowDB例外

呼叫此函數從您自己的代碼中引發類型`CDBException`異常。

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>參數

*nRetCode*<br/>
類型 RETCODE 的值,用於定義導致引發異常的錯誤類型。

*Pdb*<br/>
指向表示與異常`CDatabase`關聯的數據源連接的物件的指標。

*hstmt*<br/>
指定與異常關聯的語句句柄的 ODBC HSTMT 句柄。

### <a name="remarks"></a>備註

當從調用`AfxThrowDBException`ODBC API 函數收到 ODBC RETCODE 時,該框架會調用該框架,並將 RETCODE 解釋為特殊條件,而不是預期錯誤。 例如,數據訪問操作可能會由於磁碟讀取錯誤而失敗。

有關 ODBC 定義的 RETCODE 值的資訊,請參閱 Windows SDK 中的第 8 章"檢索狀態和錯誤資訊" 有關 MFC 延伸到這些程式碼的資訊,請參閱式[CDBException](../../mfc/reference/cdbexception-class.md)。

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="afxabort"></a><a name="afxabort"></a>阿fxAbort

MFC 提供的默認終止功能。

```
void  AfxAbort();
```

### <a name="remarks"></a>備註

`AfxAbort`當出現致命錯誤(如無法處理的未捕獲異常)時,MFC 成員函數將在內部調用。 當您遇到無法`AfxAbort`恢復的災難性錯誤時,可以在極少數情況下調用。

### <a name="example"></a>範例

請參閱[CATCH](#catch)的範例。

### <a name="requirements"></a>需求

  **標題**afx.h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[CException 類別](cexception-class.md)<br/>
[CInvalidArgException 類別](cinvalidargexception-class.md)
