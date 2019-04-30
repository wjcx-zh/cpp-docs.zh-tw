---
title: CArchiveException 類別
ms.date: 11/04/2016
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
ms.openlocfilehash: 731735bccf9225e67d82b1fe90336c92a630b368
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391305"
---
# <a name="carchiveexception-class"></a>CArchiveException 類別

表示序列化例外狀況

## <a name="syntax"></a>語法

```
class CArchiveException : public CException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|建構 `CArchiveException` 物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CArchiveException::m_cause](#m_cause)|表示例外狀況的原因。|
|[CArchiveException::m_strFileName](#m_strfilename)|指定此例外狀況的檔案名稱。|

## <a name="remarks"></a>備註

`CArchiveException`類別包含公用資料成員，表示造成例外狀況。

`CArchiveException` 物件的建構及內擲回[CArchive](../../mfc/reference/carchive-class.md)成員函式。 您可以存取這些物件的範圍內**攔截**運算式。 原因代碼與作業系統無關。 如需例外狀況處理的詳細資訊，請參閱[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="carchiveexception"></a>  CArchiveException::CArchiveException

建構`CArchiveException`物件，儲存的值*導致*物件中。

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>參數

*cause*<br/>
表示例外狀況原因的列舉型別變數。 如需列舉值的清單，請參閱 < [m_cause](#m_cause)資料成員。

*lpszArchiveName*<br/>
包含名稱的字串會指向`CArchive`造成例外狀況的物件。

### <a name="remarks"></a>備註

您可以建立`CArchiveException`在堆積上物件和自己丟或讓全域函式[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)為您處理它。

請勿直接; 使用這個建構函式相反地，呼叫全域函式`AfxThrowArchiveException`。

##  <a name="m_cause"></a>  CArchiveException::m_cause

指定例外狀況的原因。

```
int m_cause;
```

### <a name="remarks"></a>備註

此資料成員是公用類型的變數**int**。其值由定義`CArchiveException`列舉型別。 列舉程式及其意義如下：

- `CArchiveException::none` 不發生任何錯誤。

- `CArchiveException::genericException` 未指定的錯誤。

- `CArchiveException::readOnly` 嘗試寫入至載入開啟的封存。

- `CArchiveException::endOfFile` 到達的檔案結尾時讀取物件。

- `CArchiveException::writeOnly` 嘗試讀取儲存開啟的封存。

- `CArchiveException::badIndex` 無效的檔案格式。

- `CArchiveException::badClass` 嘗試讀取為物件的類型錯誤的物件。

- `CArchiveException::badSchema` 嘗試讀取具有不同版本的類別的物件。

    > [!NOTE]
    >  這些 `CArchiveException` 原因列舉程式不同於 `CFileException` 原因列舉程式。

    > [!NOTE]
    > `CArchiveException::generic` 已被取代。 請改用 `genericException`。 如果**泛型**是用在應用程式和建置以 /clr，會有不容易解密的語法錯誤。

##  <a name="m_strfilename"></a>  CArchiveException::m_strFileName

指定此例外狀況的檔案名稱。

```
CString m_strFileName;
```

## <a name="see-also"></a>另請參閱

[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CArchive 類別](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[例外狀況處理](../../mfc/reference/exception-processing.md)
