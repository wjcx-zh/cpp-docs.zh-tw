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
ms.openlocfilehash: 9d6a1c30ca0811085124a5fb5994c5f35d412ae7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837180"
---
# <a name="exception-processing"></a>例外狀況處理

當程式執行時，可能會發生一些稱為「例外狀況」的異常狀況和錯誤。 這些可能包括記憶體不足、資源配置錯誤，以及尋找檔案失敗。

MFC 程式庫使用的例外狀況處理配置，會在 c + + 的 ANSI 標準委員會所提議的模型之後緊密建立模型。 必須先設定例外狀況處理常式，才能呼叫可能會發生異常狀況的函式。 如果函數遇到異常狀況，則會擲回例外狀況，並將控制權傳遞至例外狀況處理常式。

MFC 程式庫包含的數個宏將會設定例外狀況處理常式。 如有必要，還有一些其他全域函數有助於擲回特製化例外狀況和終止程式。 這些宏和全域函式分成下列類別：

- 例外狀況宏，其結構您的例外狀況處理常式。

- 例外狀況擲回函式) ，其會產生特定類型的例外狀況。

- 終止函式，這會導致程式終止。

如需範例和詳細資訊，請參閱文章 [例外](../../mfc/exception-handling-in-mfc.md)狀況。

### <a name="exception-macros"></a>例外狀況宏

|名稱|描述|
|-|-|
|[嘗試](#try)|指定例外狀況處理的程式碼區塊。|
|[抓住](#catch)|指定程式碼區塊，以攔截先前 **TRY** 區塊中的例外狀況。|
|[CATCH_ALL](#catch_all)|指定程式碼區塊，以攔截上述 **TRY** 區塊中的所有例外狀況。|
|[AND_CATCH](#and_catch)|指定程式碼區塊，以攔截先前 **TRY** 區塊中的其他例外狀況類型。|
|[AND_CATCH_ALL](#and_catch_all)|指定程式碼區塊，以攔截先前 **TRY** 區塊中擲回的所有其他例外狀況類型。|
|[END_CATCH](#end_catch)|結束最後一個 **CATCH** 或 **AND_CATCH** 程式碼區塊。|
|[END_CATCH_ALL](#end_catch_all)|結束最後一個 **CATCH_ALL** 程式碼區塊。|
|[THROW](#throw)|擲回指定的例外狀況。|
|[THROW_LAST](#throw_last)|將目前處理的例外狀況擲回至下一個外部處理常式。|

### <a name="exception-throwing-functions"></a>例外狀況擲回函式

|名稱|描述|
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|擲回封存例外狀況。|
|[AfxThrowFileException](#afxthrowfileexception)|擲回檔案例外狀況。|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|擲回不正確引數例外狀況。|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|擲回記憶體例外狀況。|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|擲回不支援的例外狀況。|
|[AfxThrowResourceException](#afxthrowresourceexception)|擲回 Windows 資源-找不到例外狀況。|
|[AfxThrowUserException](#afxthrowuserexception)|在使用者起始的程式動作中擲回例外狀況。|

MFC 針對 OLE 例外狀況提供兩個例外狀況擲回函式：

### <a name="ole-exception-functions"></a>OLE 例外狀況函式

|名稱|描述|
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|在 OLE automation 函數中擲回例外狀況。|
|[AfxThrowOleException](#afxthrowoleexception)|擲回 OLE 例外狀況。|

為了支援資料庫例外狀況，資料庫類別提供兩個例外狀況類別、和和全域函式 `CDBException` `CDaoException` 來支援例外狀況類型：

### <a name="dao-exception-functions"></a>DAO 例外狀況函式

|名稱|描述|
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|從您自己的程式碼擲回 [CDaoException](../../mfc/reference/cdaoexception-class.md) 。|
|[AfxThrowDBException](#afxthrowdbexception)|從您自己的程式碼擲回 [CDBException](../../mfc/reference/cdbexception-class.md) 。|

MFC 提供下列終止函數：

### <a name="termination-functions"></a>終止函式

|名稱|描述|
|-|-|
|[AfxAbort](#afxabort)|在發生嚴重錯誤時呼叫以終止應用程式。|

## <a name="try"></a><a name="try"></a> 嘗試

設定 **TRY** 區塊。

```
TRY
```

### <a name="remarks"></a>備註

**TRY**區塊會識別可能會擲回例外狀況的程式碼區塊。 這些例外狀況會在下列 **CATCH** 和 **AND_CATCH** 區塊中處理。 允許遞迴：可能會忽略例外狀況，或使用 THROW_LAST 宏將例外狀況傳遞至外部 **TRY** 區塊。 使用 END_CATCH 或 END_CATCH_ALL 宏來結束 **TRY** 區塊。

如需詳細資訊，請參閱文章 [例外](../../mfc/exception-handling-in-mfc.md)狀況。

### <a name="example"></a>範例

請參閱 [CATCH](#catch)的範例。

### <a name="requirements"></a>規格需求

標頭：afx.h

## <a name="catch"></a><a name="catch"></a> 抓住

定義程式碼區塊，此區塊會攔截先前 **TRY** 區塊中擲回的第一個例外狀況類型。

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_class*<br/>
指定要測試的例外狀況類型。 如需標準例外狀況類別的清單，請參閱類別 [CException](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
指定將由巨集建立的例外狀況物件指標的名稱。 您可以使用指標名稱來存取 **CATCH** 區塊內的例外狀況物件。 會為您宣告這個變數。

### <a name="remarks"></a>備註

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 叫用 THROW_LAST 宏以將處理移至下一個外部例外狀況框架。 以 END_CATCH 宏結束 **TRY** 區塊。

如果 *exception_class* 是類別 `CException` ，則會捕捉所有例外狀況類型。 您可以使用 [CObject：： IsKindOf](../../mfc/reference/cobject-class.md#iskindof) 成員函式來判斷擲回的特定例外狀況。 若要攔截數種例外狀況，更好的方法是使用連續的 **AND_CATCH** 語句，每個語句都有不同的例外狀況類型。

例外狀況物件指標是由宏所建立。 您不需要自行進行宣告。

> [!NOTE]
> **CATCH**區塊定義為以大括弧分隔的 c + + 範圍。 如果您在這個範圍中宣告變數，變數就只能在該範圍內存取。 這也適用于 *exception_object_pointer_name*。

如需例外狀況和 CATCH 宏的詳細資訊，請參閱文章 [例外](../../mfc/exception-handling-in-mfc.md)狀況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

## <a name="catch_all"></a><a name="catch_all"></a> CATCH_ALL

定義程式碼區塊，以攔截上述 **TRY** 區塊中擲回的所有例外狀況類型。

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_object_pointer_name*<br/>
指定將由巨集建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取在 `CATCH_ALL` 區塊中的例外狀況物件。 會為您宣告這個變數。

### <a name="remarks"></a>備註

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 叫用 `THROW_LAST` 巨集將處理移位到下個外部例外狀況框架。 如果您使用 **CATCH_ALL**，請以 END_CATCH_ALL 宏結束 **TRY** 區塊。

> [!NOTE]
> **CATCH_ALL**區塊定義為以大括弧分隔的 c + + 範圍。 如果您在這個範圍中宣告變數，變數就只能在該範圍內存取。

如需例外狀況的詳細資訊，請參閱文章 [例外](../../mfc/exception-handling-in-mfc.md)狀況。

### <a name="example"></a>範例

請參閱 [CFile：： Abort](../../mfc/reference/cfile-class.md#abort)的範例。

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="and_catch"></a><a name="and_catch"></a> AND_CATCH

定義程式碼區塊，以攔截先前 **TRY** 區塊中擲回的額外例外狀況類型。

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_class*<br/>
指定要測試的例外狀況類型。 如需標準例外狀況類別的清單，請參閱類別 [CException](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
將由宏建立之例外狀況物件指標的名稱。 您可以使用指標名稱存取 **AND_CATCH** 區塊內的例外狀況物件。 會為您宣告這個變數。

### <a name="remarks"></a>備註

您可以使用 CATCH 宏來攔截一個例外狀況型別，然後使用 AND_CATCH 宏來攔截每個後續的型別。 以 END_CATCH 宏結束 **TRY** 區塊。

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 呼叫 **AND_CATCH** 區塊內的 THROW_LAST 宏，將處理移至下一個外部例外狀況框架。 **AND_CATCH** 標示之前 **CATCH** 或 **AND_CATCH** 區塊的結尾。

> [!NOTE]
> **AND_CATCH**區塊定義為 c + + 範圍， (以大括弧) 來分隔。 如果您在此範圍中宣告變數，請記住它們只能在該範圍內進行存取。 這也適用于 *exception_object_pointer_name* 變數。

### <a name="example"></a>範例

請參閱 [CATCH](#catch)的範例。

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="and_catch_all"></a><a name="and_catch_all"></a> AND_CATCH_ALL

定義程式碼區塊，以攔截先前 **TRY** 區塊中擲回的額外例外狀況類型。

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_object_pointer_name*<br/>
將由宏建立之例外狀況物件指標的名稱。 您可以使用指標名稱存取 **AND_CATCH_ALL** 區塊內的例外狀況物件。 會為您宣告這個變數。

### <a name="remarks"></a>備註

您可以使用 **catch** 宏來攔截一個例外狀況類型，然後使用 AND_CATCH_ALL 宏來攔截所有其他後續的類型。 如果您使用 AND_CATCH_ALL，請以 END_CATCH_ALL 宏結束 **TRY** 區塊。

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 呼叫 **AND_CATCH_ALL** 區塊內的 THROW_LAST 宏，將處理移至下一個外部例外狀況框架。 **AND_CATCH_ALL** 標示之前 **CATCH** 或 **AND_CATCH_ALL** 區塊的結尾。

> [!NOTE]
> **AND_CATCH_ALL**區塊定義為 c + + 範圍， (以大括弧) 分隔。 如果您在此範圍中宣告變數，請記住它們只能在該範圍內進行存取。

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="end_catch"></a><a name="end_catch"></a> END_CATCH

標示最後一個 **CATCH** 或 **AND_CATCH** 區塊的結尾。

```
END_CATCH
```

### <a name="remarks"></a>備註

如需 END_CATCH 宏的詳細資訊，請參閱文章 [例外](../../mfc/exception-handling-in-mfc.md)狀況。

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="end_catch_all"></a><a name="end_catch_all"></a> END_CATCH_ALL

標示最後一個 **CATCH_ALL88** 或 **AND_CATCH_ALL** 區塊的結尾。

```
END_CATCH_ALL
```

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="throw-mfc"></a><a name="throw"></a> 擲回 (MFC) 

擲回指定的例外狀況。

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>參數

*exception_object_pointer*<br/>
指向衍生自的例外狀況物件 `CException` 。

### <a name="remarks"></a>備註

**擲** 回中斷程式執行，並將控制項傳遞至程式中的關聯 **CATCH** 區塊。 如果您未提供 **CATCH** 區塊，則會將 control 傳遞給會列印錯誤訊息並結束的 MFC 程式庫模組。

如需詳細資訊，請參閱文章 [例外](../../mfc/exception-handling-in-mfc.md)狀況。

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="throw_last"></a><a name="throw_last"></a> THROW_LAST

將例外狀況擲回至下一個外部 **CATCH** 區塊。

```
THROW_LAST()
```

### <a name="remarks"></a>備註

這個宏可讓您擲回本機建立的例外狀況。 如果您嘗試擲回您剛剛攔截到的例外狀況，通常會離開範圍並予以刪除。 使用 **THROW_LAST**時，會正確地將例外狀況傳遞給下一個 **CATCH** 處理常式。

如需詳細資訊，請參閱文章 [例外](../../mfc/exception-handling-in-mfc.md)狀況。

### <a name="example"></a>範例

請參閱 [CFile：： Abort](../../mfc/reference/cfile-class.md#abort)的範例。

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="afxthrowarchiveexception"></a><a name="afxthrowarchiveexception"></a> AfxThrowArchiveException

擲回封存例外狀況。

```cpp
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>參數

*原因*<br/>
指定表示例外狀況原因的整數。 如需可能值的清單，請參閱 [CArchiveException：： m_cause](../../mfc/reference/carchiveexception-class.md#m_cause)。

*lpszArchiveName*<br/>
指向包含造成例外狀況之物件名稱的字串 `CArchive` （如果有的話)  (）。

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="afxthrowfileexception"></a><a name="afxthrowfileexception"></a> AfxThrowFileException

擲回檔案例外狀況。

```cpp
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>參數

*原因*<br/>
指定表示例外狀況原因的整數。 如需可能值的清單，請參閱 [CFileException：： m_cause](../../mfc/reference/cfileexception-class.md#m_cause)。

*lOsError*<br/>
包含作業系統錯誤號碼 (如果可用) 指出例外狀況的原因。 請參閱您的作業系統手冊，以取得錯誤碼清單。

*lpszFileName*<br/>
指向包含造成例外狀況之檔案名的字串， (（如果有的話）) 。

### <a name="remarks"></a>備註

您必須負責根據作業系統錯誤碼來判斷原因。

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="afxthrowinvalidargexception"></a><a name="afxthrowinvalidargexception"></a> AfxThrowInvalidArgException

擲回不正確引數例外狀況。

### <a name="syntax"></a>語法

```cpp
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>備註

使用不正確引數時，會呼叫此函數。

### <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="afxthrowmemoryexception"></a><a name="afxthrowmemoryexception"></a> AfxThrowMemoryException

擲回記憶體例外狀況。

```cpp
void AfxThrowMemoryException();
```

### <a name="remarks"></a>備註

如果對基礎系統記憶體配置器的呼叫 (例如 **malloc** 和 [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows 函式) 失敗，則呼叫此函式。 您不需要呼叫它， **`new`** 因為 **`new`** 如果記憶體配置失敗，將會自動擲回記憶體例外狀況。

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="afxthrownotsupportedexception"></a><a name="afxthrownotsupportedexception"></a> AfxThrowNotSupportedException

擲回例外狀況，此例外狀況是要求不支援的功能的結果。

```cpp
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="afxthrowresourceexception"></a><a name="afxthrowresourceexception"></a> AfxThrowResourceException

擲回資源例外狀況。

```cpp
void  AfxThrowResourceException();
```

### <a name="remarks"></a>備註

這項功能通常會在無法載入 Windows 資源時呼叫。

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="afxthrowuserexception"></a><a name="afxthrowuserexception"></a> AfxThrowUserException

擲回例外狀況，以停止終端使用者操作。

```cpp
void AfxThrowUserException();
```

### <a name="remarks"></a>備註

這項功能通常會在 `AfxMessageBox` 向使用者回報錯誤之後立即呼叫。

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="afxthrowoledispatchexception"></a><a name="afxthrowoledispatchexception"></a> AfxThrowOleDispatchException

使用此函式在 OLE Automation 函式內擲回例外狀況。

```cpp
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

*wCode*<br/>
應用程式特定的錯誤碼。

*lpszDescription*<br/>
錯誤的詳細描述。

*nDescriptionID*<br/>
詳細錯誤描述的資源 ID。

*nHelpID*<br/>
您的應用程式說明 (.HLP) 檔的說明內容。

### <a name="remarks"></a>備註

提供給此函式的資訊可以透過驅動應用程式 (Microsoft Visual Basic 或其他 OLE Automation 用戶端應用程式) 來加以顯示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="afxthrowoleexception"></a><a name="afxthrowoleexception"></a> AfxThrowOleException

建立類型的物件 `COleException` ，並擲回例外狀況。

```cpp
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>參數

*Sc*<br/>
表示例外狀況原因的 OLE 狀態碼。

*小時*<br/>
結果碼的控制碼，指出例外狀況的原因。

### <a name="remarks"></a>備註

以 HRESULT 作為引數的版本會將該結果程式碼轉換成對應的 SCODE。 如需 HRESULT 和 SCODE 的詳細資訊，請參閱 Windows SDK 中 [COM 錯誤碼的結構](/windows/win32/com/structure-of-com-error-codes) 。

### <a name="requirements"></a>規格需求

  **標頭** afxdao。h

## <a name="afxthrowdaoexception"></a><a name="afxthrowdaoexception"></a> AfxThrowDaoException

呼叫此函式，從您自己的程式碼擲回類型 [CDaoException](../../mfc/reference/cdaoexception-class.md) 的例外狀況。

```cpp
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>參數

*nAfxDaoError*<br/>
代表 DAO 擴充錯誤碼的整數值，可以是 [CDaoException：： m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)下所列的其中一個值。

*scode*<br/>
DAO 的 OLE 錯誤碼，屬於 SCODE 類型。 如需詳細資訊，請參閱 [CDaoException：： m_scode](../../mfc/reference/cdaoexception-class.md#m_scode)。

### <a name="remarks"></a>備註

架構也會呼叫 `AfxThrowDaoException` 。 在您的呼叫中，您可以傳遞其中一個參數或兩者。 例如，如果您想要引發 **CDaoException：： nAfxDaoError** 中定義的其中一個錯誤，但不在意 *scode* 參數，請在 *nAfxDaoError* 參數中傳遞有效的程式碼，並接受 *scode*的預設值。

如需 MFC DAO 類別相關例外狀況的詳細資訊，請參閱 `CDaoException` 本書中的類別和文章 [例外狀況：資料庫例外](../../mfc/exceptions-database-exceptions.md)狀況。

### <a name="requirements"></a>規格需求

  **標頭** afxdb.h。h

## <a name="afxthrowdbexception"></a><a name="afxthrowdbexception"></a> AfxThrowDBException

從您自己的程式碼呼叫此函式，以擲回類型的例外狀況 `CDBException` 。

```cpp
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>參數

*nRetCode*<br/>
RETCODE 類型的值，定義造成擲回例外狀況之錯誤的類型。

*Pdb*<br/>
物件的指標 `CDatabase` ，該物件代表與例外狀況相關聯的資料來源連接。

*hstmt*<br/>
ODBC HSTMT 控制碼，指定與例外狀況相關聯的語句控制碼。

### <a name="remarks"></a>備註

架構會在 `AfxThrowDBException` 從 ODBC API 函式的呼叫接收 ODBC RETCODE 時呼叫，並將 RETCODE 解釋為例外狀況，而不是 expectable 錯誤。 例如，資料存取作業可能會因為磁片讀取錯誤而失敗。

如需有關 ODBC 所定義之 RETCODE 值的詳細資訊，請參閱 Windows SDK 中的第8章「正在取得狀態和錯誤資訊」。 如需這些程式碼的 MFC 擴充功能的詳細資訊，請參閱類別 [CDBException](../../mfc/reference/cdbexception-class.md)。

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="afxabort"></a><a name="afxabort"></a> AfxAbort

MFC 提供的預設終止函式。

```cpp
void  AfxAbort();
```

### <a name="remarks"></a>備註

`AfxAbort` 當發生嚴重錯誤（例如無法處理的未攔截例外狀況）時，MFC 成員函式會在內部呼叫。 `AfxAbort`當您遇到無法復原的嚴重錯誤時，可以在罕見的情況下呼叫。

### <a name="example"></a>範例

請參閱 [CATCH](#catch)的範例。

### <a name="requirements"></a>規格需求

  **標頭** afx。h

## <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[CException 類別](cexception-class.md)<br/>
[CInvalidArgException 類別](cinvalidargexception-class.md)
