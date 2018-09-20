---
title: 例外狀況處理 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.exceptions
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1711e634fca1b4350e8aca5f75f0de8a4b3a0e5f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417354"
---
# <a name="exception-processing"></a>例外狀況處理

當程式執行時，可能會發生異常狀況和稱為 「 例外狀況 」 的錯誤數目。 這些可能包括用盡記憶體、 資源配置錯誤，以及找不到檔案。

Microsoft Foundation 類別庫會使用仿造自密切所提議由 ANSI 標準委員會的 c + + 例外狀況處理配置。 例外狀況處理常式必須設定之前，呼叫函式可能會發生異常狀況。 如果函式發生異常狀況，就會擲回例外狀況，控制權會傳遞給例外狀況處理常式。

包含 Microsoft Foundation Class Library 的數個巨集將會設定例外狀況處理常式。 如有必要，擲回特定例外狀況和終止程式，幫助其他全域函式的數目。 這些巨集和全域函式可分成下列類別：

- 例外狀況巨集： 結構，您的例外狀況處理常式。

- Exception-throwing 函式)，這會產生特定類型的例外狀況。

- 終止函式，這會導致程式終止。

如需範例和詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。

### <a name="exception-macros"></a>例外狀況巨集

|||
|-|-|
|[請嘗試](#try)|將指定的例外狀況處理的程式碼區塊。|
|[CATCH](#catch)|指定的程式碼來攔截來自上述例外狀況區塊**嘗試**區塊。|
|[CATCH_ALL](#catch_all)|將指定來攔截所有例外狀況，從先前的程式碼區塊**嘗試**區塊。|
|[AND_CATCH](#and_catch)|將指定來攔截來自上述的其他例外狀況類型的程式碼區塊**嘗試**區塊。|
|[AND_CATCH_ALL](#and_catch_all)|將指定來攔截所有其他先前擲回的其他例外狀況類型的程式碼區塊**嘗試**區塊。|
|[END_CATCH](#end_catch)|結束上次**攔截**或是**AND_CATCH**程式碼區塊。|
|[END_CATCH_ALL](#end_catch_all)|結束上次**CATCH_ALL**程式碼區塊。|
|[擲回](#throw)|指定的例外狀況會擲回。|
|[THROW_LAST](#throw_last)|目前處理的例外狀況下, 一步 外部的處理常式會擲回。|

### <a name="exception-throwing-functions"></a>擲回例外狀況的函式

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|封存例外狀況會擲回。|
|[AfxThrowFileException](#afxthrowfileexception)|檔案例外狀況會擲回。|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|無效的引數例外狀況會擲回。|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|會擲回記憶體例外狀況。|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|不支援的例外狀況會擲回。|
|[AfxThrowResourceException](#afxthrowresourceexception)|Windows 找不到資源例外狀況會擲回。|
|[AfxThrowUserException](#afxthrowuserexception)|在使用者啟動程式的動作中，會發生例外狀況。|

MFC 提供兩個擲回例外狀況的函式，專為 OLE 例外狀況：

### <a name="ole-exception-functions"></a>OLE 例外狀況函式

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|擲回例外狀況中的 OLE automation 函式。|
|[AfxThrowOleException](#afxthrowoleexception)|OLE 例外狀況會擲回。|

若要支援資料庫例外狀況，資料庫類別提供兩個例外狀況類別：`CDBException`和`CDaoException`，和全域函式，以支援例外狀況類型：

### <a name="dao-exception-functions"></a>DAO 例外狀況函式

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|會擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)從您自己的程式碼。|
|[AfxThrowDBException](#afxthrowdbexception)|會擲回[CDBException](../../mfc/reference/cdbexception-class.md)從您自己的程式碼。|

MFC 提供下列的終止函式：

### <a name="termination-functions"></a>終止函式

|||
|-|-|
|[AfxAbort](#afxabort)|呼叫終止應用程式發生嚴重錯誤時，就會發生。|

##  <a name="try"></a>  請嘗試

設定**嘗試**區塊。

```
TRY
```

### <a name="remarks"></a>備註

A**嘗試**區塊識別可能會擲回例外狀況的程式碼區塊。 在下列處理這些例外狀況**攔截**並**AND_CATCH**區塊。 允許遞迴： 例外狀況可能會傳遞至外部**嘗試**區塊時，略過它們，或使用 THROW_LAST 巨集。 結束**嘗試**END_CATCH 或 END_CATCH_ALL 巨集的區塊。

如需詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。

### <a name="example"></a>範例

範例，請參閱[攔截](#catch)。

### <a name="requirements"></a>需求

標頭：afx.h

##  <a name="catch"></a>  CATCH

定義會攔截擲回先前的第一個例外狀況類型的程式碼區塊**嘗試**區塊。

```
CATCH(exception_class, exception_object_pointer_name)

```

### <a name="parameters"></a>參數

*exception_class*<br/>
指定要測試的例外狀況類型。 如需標準例外狀況類別的清單，請參閱類別[CException](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
指定將由巨集建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取例外狀況物件內**攔截**區塊。 會為您宣告這個變數。

### <a name="remarks"></a>備註

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 叫用 THROW_LAST 巨集，將處理移位到下一個外部例外狀況框架。 結束**嘗試**END_CATCH 巨集的區塊。

如果*exception_class*是類別`CException`，則會攔截所有例外狀況類型。 您可以使用[cobject:: Iskindof](../../mfc/reference/cobject-class.md#iskindof)成員函式，來判斷哪一個特定的例外狀況。 若要攔截例外狀況的幾種更好的方法是使用循序**AND_CATCH**陳述式，各有不同的例外狀況類型。

例外狀況物件指標會由巨集。 您不需要自行進行宣告。

> [!NOTE]
>  **攔截**區塊會定義為 c + + 範圍括號括住分隔。 如果您在這個範圍中宣告變數，變數就只能在該範圍內存取。 這也適用於*exception_object_pointer_name*。

如需有關例外狀況和 CATCH 巨集的詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

##  <a name="catch_all"></a>  CATCH_ALL

定義會攔截所有例外狀況類型擲回先前的程式碼區塊**嘗試**區塊。

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_object_pointer_name*<br/>
指定將由巨集建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取在 `CATCH_ALL` 區塊中的例外狀況物件。 會為您宣告這個變數。

### <a name="remarks"></a>備註

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 叫用 `THROW_LAST` 巨集將處理移位到下個外部例外狀況框架。 如果您使用**CATCH_ALL**，結束**嘗試**END_CATCH_ALL 巨集的區塊。

> [!NOTE]
>  **CATCH_ALL**區塊會定義為 c + + 範圍括號括住分隔。 如果您在這個範圍中宣告變數，變數就只能在該範圍內存取。

如需有關例外狀況的詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。

### <a name="example"></a>範例

範例，請參閱[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。

### <a name="requirements"></a>需求

  **標頭**afx.h

##  <a name="and_catch"></a>  AND_CATCH

定義來攔截在先前會擲回其他例外狀況類型的程式碼區塊**嘗試**區塊。

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_class*<br/>
指定要測試的例外狀況類型。 如需標準例外狀況類別的清單，請參閱類別[CException](../../mfc/reference/cexception-class.md)。

*exception_object_pointer_name*<br/>
將巨集所建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取例外狀況物件內**AND_CATCH**區塊。 會為您宣告這個變數。

### <a name="remarks"></a>備註

使用 CATCH 巨集，以攔截例外狀況類型，則 AND_CATCH 巨集，來攔截每個後續的型別。 結束**嘗試**END_CATCH 巨集的區塊。

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 呼叫內 THROW_LAST 巨集**AND_CATCH**封鎖轉移至下一個外部例外狀況框架處理。 **AND_CATCH**先前的結束標記**攔截**或是**AND_CATCH**區塊。

> [!NOTE]
>  **AND_CATCH**區塊會定義為 c + + 範圍 （大括號括住分隔）。 如果您宣告這個範圍中的變數，請記得它們是只能在該範圍內存取。 這也適用於*exception_object_pointer_name*變數。

### <a name="example"></a>範例

範例，請參閱[攔截](#catch)。

### <a name="requirements"></a>需求

  **標頭**afx.h
##  <a name="and_catch_all"></a>  AND_CATCH_ALL

定義來攔截在先前會擲回其他例外狀況類型的程式碼區塊**嘗試**區塊。

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>參數

*exception_object_pointer_name*<br/>
將巨集所建立的例外狀況物件指標的名稱。 您可以使用指標名稱存取例外狀況物件內**AND_CATCH_ALL**區塊。 會為您宣告這個變數。

### <a name="remarks"></a>備註

使用**攔截**巨集來攔截例外狀況類型，則 AND_CATCH_ALL 巨集，來攔截所有其他後續的類型。 如果您使用 AND_CATCH_ALL，結束**嘗試**END_CATCH_ALL 巨集的區塊。

處理例外狀況的程式碼可以查閱例外狀況物件，如果可行，取得關於例外狀況特定原因的詳細資訊。 呼叫內 THROW_LAST 巨集**AND_CATCH_ALL**封鎖轉移至下一個外部例外狀況框架處理。 **AND_CATCH_ALL**先前的結束標記**攔截**或是**AND_CATCH_ALL**區塊。

> [!NOTE]
>  **AND_CATCH_ALL**區塊會定義為 c + + 範圍 （大括號分隔）。 如果您宣告這個範圍中的變數，請記得它們是只能在該範圍內存取。

### <a name="requirements"></a>需求

  **標頭**afx.h

##  <a name="end_catch"></a>  END_CATCH

最後一個結束標記**攔截**或是**AND_CATCH**區塊。

```
END_CATCH
```

### <a name="remarks"></a>備註

如需有關 END_CATCH 巨集的詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。

### <a name="requirements"></a>需求

  **標頭**afx.h

##  <a name="end_catch_all"></a>  END_CATCH_ALL

標記結尾的最後一個 * * CATCH_ALL88 或**AND_CATCH_ALL**區塊。

```
END_CATCH_ALL
```

### <a name="requirements"></a>需求

  **標頭**afx.h

##  <a name="throw"></a>  擲回 (MFC)

指定的例外狀況會擲回。

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>參數

*exception_object_pointer*<br/>
指向例外狀況物件衍生自`CException`。

### <a name="remarks"></a>備註

**擲回**中斷應用程式執行時，將控制權傳遞至相關聯**攔截**封鎖您的程式中。 如果您未提供**攔截**封鎖，則控制權會傳遞至 Microsoft Foundation 類別程式庫模組會列印錯誤訊息並結束。

如需詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。

### <a name="requirements"></a>需求

  **標頭**afx.h

##  <a name="throw_last"></a>  THROW_LAST

重新擲回例外狀況，下一步 以外部**攔截**區塊。

```
THROW_LAST()
```

### <a name="remarks"></a>備註

這個巨集可讓您將在本機建立的例外狀況。 如果您嘗試將會擲回，只要攔截到例外狀況，它通常會移出範圍，並刪除。 具有**THROW_LAST**，例外狀況已正確地傳遞至下一個**攔截**處理常式。

如需詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。

### <a name="example"></a>範例

範例，請參閱[cfile:: Abort](../../mfc/reference/cfile-class.md#abort)。

### <a name="requirements"></a>需求

  **標頭**afx.h

##  <a name="afxthrowarchiveexception"></a>  AfxThrowArchiveException

封存例外狀況會擲回。

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>參數

*原因*<br/>
指定一個整數，表示例外狀況的原因。 如需可能的值，請參閱[CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause)。

*lpszArchiveName*<br/>
包含名稱的字串會指向`CArchive`造成例外狀況 （如果有的話） 的物件。

### <a name="requirements"></a>需求

  **標頭**afx.h

##  <a name="afxthrowfileexception"></a>  AfxThrowFileException

檔案例外狀況會擲回。

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>參數

*原因*<br/>
指定一個整數，表示例外狀況的原因。 如需可能的值，請參閱[CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause)。

*lOsError*<br/>
包含的作業系統錯誤號碼 （如果有的話），說明例外狀況的原因。 請參閱作業系統手冊，如需錯誤碼的清單。

*lpszFileName*<br/>
指向字串，包含造成例外狀況 （如果有的話） 的檔案名稱。

### <a name="remarks"></a>備註

您有責任判斷作業系統錯誤程式碼為基礎的原因。

### <a name="requirements"></a>需求

  **標頭**afx.h

## <a name="afxthrowinvalidargexception"></a>  AfxThrowInvalidArgException

無效的引數例外狀況會擲回。

### <a name="syntax"></a>語法

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>備註

無效的引數使用時，會呼叫此函數。

### <a name="requirements"></a>需求

**標頭：** afx.h

### <a name="see-also"></a>另請參閱

[巨集和全域](mfc-macros-and-globals.md)<br/>
[CInvalidArgException 類別](cinvalidargexception-class.md)<br/>
[擲回](#throw)


##  <a name="afxthrowmemoryexception"></a>  AfxThrowMemoryException

會擲回記憶體例外狀況。

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>備註

呼叫此函式，如果呼叫基礎的系統記憶體配置器 (例如**malloc**並[GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) Windows 函式) 失敗。 您不需要呼叫它**新**因為**新**會擲回記憶體例外狀況會自動在記憶體配置失敗。

### <a name="requirements"></a>需求

  **標頭**afx.h

##  <a name="afxthrownotsupportedexception"></a>  AfxThrowNotSupportedException

會擲回的例外狀況，不支援的功能要求的結果。

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>需求

  **標頭**afx.h

##  <a name="afxthrowresourceexception"></a>  AfxThrowResourceException

資源例外狀況會擲回。

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>備註

無法載入 Windows 資源時，通常會呼叫此函數。

### <a name="requirements"></a>需求

  **標頭**afx.h

##  <a name="afxthrowuserexception"></a>  AfxThrowUserException

會擲回例外狀況停止使用者作業。

```
void AfxThrowUserException();
```

### <a name="remarks"></a>備註

此函式通常會呼叫之後立即`AfxMessageBox`向使用者回報了錯誤。

### <a name="requirements"></a>需求

  **標頭**afx.h

##  <a name="afxthrowoledispatchexception"></a>  AfxThrowOleDispatchException

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

*WCode*<br/>
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

### <a name="requirements"></a>需求

  **標頭**afx.h

##  <a name="afxthrowoleexception"></a>  AfxThrowOleException

建立型別的物件`COleException`並擲回例外狀況。

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>參數

*sc*<br/>
OLE 狀態碼指出例外狀況的原因。

*hr*<br/>
處理結果的程式碼，指出例外狀況的原因。

### <a name="remarks"></a>備註

以 hresult 做為引數的版本會將該結果程式碼轉換成對應的 SCODE。 如需有關 HRESULT 和 SCODE 的詳細資訊，請參閱[錯誤碼的結構 COM](/windows/desktop/com/structure-of-com-error-codes) Windows SDK 中。

### <a name="requirements"></a>需求

  **標頭**afxdao.h

##  <a name="afxthrowdaoexception"></a>  AfxThrowDaoException

呼叫此函式會擲回例外狀況型別的[CDaoException](../../mfc/reference/cdaoexception-class.md)從您自己的程式碼。

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>參數

*nAfxDaoError*<br/>
整數值，表示擴充錯誤碼 DAO，這可以其中一個值下方[CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)。

*scode*<br/>
從 DAO，型別 SCODE OLE 錯誤程式碼。 如需資訊，請參閱[CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode)。

### <a name="remarks"></a>備註

此架構也會呼叫`AfxThrowDaoException`。 在您呼叫中，您可以傳遞參數之一或兩者。 例如，如果您想要引發的其中一個錯誤中定義**CDaoException::nAfxDaoError**但您不在意*scode*參數，傳遞有效的程式碼中*nAfxDaoError*參數並接受預設值*scode*。

如需 MFC DAO 類別相關的例外狀況資訊，請參閱類別`CDaoException`這本書和文件中[例外狀況： 資料庫例外狀況](../../mfc/exceptions-database-exceptions.md)。

### <a name="requirements"></a>需求

  **標頭**afxdb.h

##  <a name="afxthrowdbexception"></a>  AfxThrowDBException

呼叫此函式會擲回例外狀況型別的`CDBException`從您自己的程式碼。

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>參數

*nRetCode*<br/>
RETCODE，定義類型的錯誤導致擲回例外狀況類型的值。

*pdb*<br/>
指標`CDatabase`物件，表示與例外狀況相關聯的資料來源連接。

*hstmt*<br/>
指定與例外狀況相關聯的陳述式控制代碼 ODBC HSTMT 控制代碼。

### <a name="remarks"></a>備註

這個架構會呼叫`AfxThrowDBException`當 ODBC RETCODE 收到呼叫 ODBC API 函式，並將 RETCODE 解譯為例外狀況，而不是 expectable 錯誤。 例如，資料存取作業可能會失敗，因為磁碟讀取時發生錯誤。

如 ODBC 所定義之 RETCODE 值的相關資訊，請參閱 Windows SDK 中的第 8 章 「 擷取狀態和錯誤資訊 」。 如需 MFC 擴充功能，以這些程式碼的資訊，請參閱類別[CDBException](../../mfc/reference/cdbexception-class.md)。

### <a name="requirements"></a>需求

  **標頭**afx.h

##  <a name="afxabort"></a>  AfxAbort

由 MFC 提供預設的終止函式。

```
void  AfxAbort();
```

### <a name="remarks"></a>備註

`AfxAbort` 由內部呼叫 MFC 的成員函式時沒有嚴重的錯誤，例如未攔截到例外狀況無法處理。 您可以呼叫`AfxAbort`在罕見的情況下，如果您遇到重大錯誤無法復原。

### <a name="example"></a>範例

範例，請參閱[攔截](#catch)。

### <a name="requirements"></a>需求

  **標頭**afx.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)
