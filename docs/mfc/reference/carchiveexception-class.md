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
ms.openlocfilehash: 68f64cfd7dc96da04fcc0945a6b996eab4101487
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231880"
---
# <a name="carchiveexception-class"></a>CArchiveException 類別

表示序列化例外狀況

## <a name="syntax"></a>語法

```
class CArchiveException : public CException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|建構 `CArchiveException` 物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[CArchiveException：： m_cause](#m_cause)|指出例外狀況的原因。|
|[CArchiveException：： m_strFileName](#m_strfilename)|指定此例外狀況條件的檔案名。|

## <a name="remarks"></a>備註

`CArchiveException`類別包含表示例外狀況原因的公用資料成員。

`CArchiveException`物件是在[CArchive](../../mfc/reference/carchive-class.md)成員函式內進行結構化和擲回。 您可以在**CATCH**運算式的範圍記憶體取這些物件。 原因程式碼與作業系統無關。 如需例外狀況處理的詳細資訊，請參閱[例外狀況處理（MFC）](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>需求

**標頭：** afx。h

## <a name="carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a>CArchiveException::CArchiveException

會建立 `CArchiveException` 物件，並將*原因*的值儲存在物件中。

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>參數

*原因*<br/>
列舉類型變數，指出例外狀況的原因。 如需列舉值的清單，請參閱[m_cause](#m_cause)資料成員。

*lpszArchiveName*<br/>
指向包含造成例外狀況之物件名稱的字串 `CArchive` 。

### <a name="remarks"></a>備註

您可以 `CArchiveException` 在堆積上建立物件並自行擲回，或讓全域函式[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)為您處理。

請勿直接使用此函數;請改為呼叫全域函式 `AfxThrowArchiveException` 。

## <a name="carchiveexceptionm_cause"></a><a name="m_cause"></a>CArchiveException：： m_cause

指定例外狀況的原因。

```
int m_cause;
```

### <a name="remarks"></a>備註

此資料成員是類型的公用變數 **`int`** 。 其值是由列舉型別所定義 `CArchiveException` 。 列舉程式及其意義如下：

- `CArchiveException::none`未發生任何錯誤。

- `CArchiveException::genericException`未指定的錯誤。

- `CArchiveException::readOnly`嘗試寫入已開啟要載入的封存。

- `CArchiveException::endOfFile`讀取物件時到達檔案結尾。

- `CArchiveException::writeOnly`嘗試從開啟的封存讀取以儲存。

- `CArchiveException::badIndex`不正確檔案格式。

- `CArchiveException::badClass`嘗試將物件讀入錯誤類型的物件中。

- `CArchiveException::badSchema`嘗試讀取具有不同版本類別的物件。

    > [!NOTE]
    >  這些 `CArchiveException` 原因列舉程式不同於 `CFileException` 原因列舉程式。

    > [!NOTE]
    > `CArchiveException::generic` 已被取代。 請改用 `genericException`。 如果在應用程式中使用**泛型**，並以/clr 建立，則會有不容易解密的語法錯誤。

## <a name="carchiveexceptionm_strfilename"></a><a name="m_strfilename"></a>CArchiveException：： m_strFileName

指定此例外狀況條件的檔案名。

```
CString m_strFileName;
```

## <a name="see-also"></a>另請參閱

[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CArchive 類別](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[例外狀況處理](../../mfc/reference/exception-processing.md)
