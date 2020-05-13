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
ms.openlocfilehash: ad2a9d8c5b4466a04b5a88fcce7679911bf1b81a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377005"
---
# <a name="carchiveexception-class"></a>CArchiveException 類別

顯示序列化異常條件

## <a name="syntax"></a>語法

```
class CArchiveException : public CException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 壓縮檔例外:C 存檔例外](#carchiveexception)|建構 `CArchiveException` 物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C壓縮檔例外::m_cause](#m_cause)|指示異常原因。|
|[C存檔例外::m_strFileName](#m_strfilename)|指定此異常條件的檔案名稱。|

## <a name="remarks"></a>備註

類`CArchiveException`包括指示異常原因的公共數據成員。

`CArchiveException`物件在[CArchive](../../mfc/reference/carchive-class.md)成員函數中構造和引發。 您可以在**CATCH**表達式的範圍內訪問這些物件。 原因代碼獨立於操作系統。 有關異常處理的詳細資訊,請參閱[異常處理 (MFC)。](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a>C 壓縮檔例外:C 存檔例外

構造`CArchiveException`物件,將*原因*的值存儲在物件中。

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>參數

*cause*<br/>
指示異常原因的枚舉類型變數。 有關枚舉器的清單,請參閱[m_cause](#m_cause)資料成員。

*lpsz 壓縮檔名稱*<br/>
指向包含引起異常`CArchive`的物件名稱的字串。

### <a name="remarks"></a>備註

您可以在堆上創建`CArchiveException`一個對象,然後自己引發它,或者讓全域函數[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)為您處理它。

不要直接使用此構造函數;相反,呼叫全域函數`AfxThrowArchiveException`。

## <a name="carchiveexceptionm_cause"></a><a name="m_cause"></a>C壓縮檔例外::m_cause

指定異常的原因。

```
int m_cause;
```

### <a name="remarks"></a>備註

此數據成員是**int**類型的公共變數。其值由`CArchiveException`枚舉類型定義。 列舉程式及其意義如下：

- `CArchiveException::none`未發生錯誤。

- `CArchiveException::genericException`未指定錯誤。

- `CArchiveException::readOnly`嘗試寫入打開的存檔以進行載入。

- `CArchiveException::endOfFile`讀取物件時到達檔結尾。

- `CArchiveException::writeOnly`嘗試從打開的存檔中讀取以供存儲。

- `CArchiveException::badIndex`無效的檔案格式。

- `CArchiveException::badClass`嘗試將物件讀取到類型錯誤的物件中。

- `CArchiveException::badSchema`嘗試讀取具有類不同版本的物件。

    > [!NOTE]
    >  這些 `CArchiveException` 原因列舉程式不同於 `CFileException` 原因列舉程式。

    > [!NOTE]
    > `CArchiveException::generic` 已被取代。 請改用 `genericException`。 如果在應用程式中使用**泛型**並且使用 /clr 構建,則會有不容易破譯的語法錯誤。

## <a name="carchiveexceptionm_strfilename"></a><a name="m_strfilename"></a>C存檔例外::m_strFileName

指定此異常條件的檔案名稱。

```
CString m_strFileName;
```

## <a name="see-also"></a>另請參閱

[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CArchive 類別](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[例外狀況處理](../../mfc/reference/exception-processing.md)
