---
title: CSimpleException 類別
ms.date: 11/04/2016
f1_keywords:
- CSimpleException
- AFX/CSimpleException
- AFX/CSimpleException::CSimpleException
- AFX/CSimpleException::GetErrorMessage
helpviewer_keywords:
- CSimpleException [MFC], CSimpleException
- CSimpleException [MFC], GetErrorMessage
ms.assetid: be0eb8ef-e5b9-47d6-b0fb-efaff2d1e666
ms.openlocfilehash: afd83c1ddd6f68b10c5cc8c47c0e939bbd01b6c2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840709"
---
# <a name="csimpleexception-class"></a>CSimpleException 類別

這個類別是資源關鍵 MFC 例外狀況的基底類別。

## <a name="syntax"></a>語法

```
class AFX_NOVTABLE CSimpleException : public CException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CSimpleException：： CSimpleException](#csimpleexception)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSimpleException：： GetErrorMessage](#geterrormessage)|提供所發生錯誤的相關文字。|

## <a name="remarks"></a>備註

`CSimpleException` 是資源關鍵 MFC 例外狀況的基類，可處理錯誤訊息的擁有權和初始化。 下列類別會使用 `CSimpleException` 做為其基類：

|名稱|描述|
|-|-|
|[CMemoryException 類別](../../mfc/reference/cmemoryexception-class.md)|記憶體不足例外狀況|
|[CNotSupportedException 類別](../../mfc/reference/cnotsupportedexception-class.md)|要求不支援的作業|
|[CResourceException 類別](../../mfc/reference/cresourceexception-class.md)|找不到或無法為 Windows 資源|
|[CUserException 類別](../../mfc/reference/cuserexception-class.md)|指出找不到資源的例外狀況|
|[CInvalidArgException 類別](../../mfc/reference/cinvalidargexception-class.md)|指出無效引數的例外狀況|

因為 `CSimpleException` 是抽象基類，所以您無法 `CSimpleException` 直接宣告物件。 相反地，您必須宣告衍生的物件，例如上表中的物件。 如果您要宣告自己的衍生類別，請使用先前的類別做為模型。

如需詳細資訊，請參閱 [CException 類別](../../mfc/reference/cexception-class.md) 主題和 [例外狀況處理 (MFC) ](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>規格需求

**標頭：** afx。h

## <a name="csimpleexceptioncsimpleexception"></a><a name="csimpleexception"></a> CSimpleException：： CSimpleException

建構函式。

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>參數

*bAutoDelete*<br/>
如果已在堆積上設定物件的記憶體，請指定 TRUE `CSimpleException` 。 這會導致在 `CSimpleException` `Delete` 呼叫成員函式來刪除例外狀況時，刪除物件。 如果 `CSimpleException` 物件在堆疊上或為全域物件，請指定 FALSE。 在此情況下， `CSimpleException` 當呼叫成員函式時，不會刪除物件 `Delete` 。

### <a name="remarks"></a>備註

您通常不需要直接呼叫此函式。 擲回例外狀況的函式應該建立衍生類別的實例， `CException` 並呼叫其函式，或是使用其中一個 MFC throw 函數（例如 [AfxThrowFileException](exception-processing.md#afxthrowfileexception)）來擲回預先定義的類型。

## <a name="csimpleexceptiongeterrormessage"></a><a name="geterrormessage"></a> CSimpleException：： GetErrorMessage

呼叫此成員函式，以提供所發生錯誤的相關文字。

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>參數

*lpszError*<br/>
將會收到錯誤訊息的緩衝區指標。

*nMaxError*<br/>
緩衝區可以容納的字元數上限，包括 Null 結束字元。

*pnHelpCoNtext*<br/>
將接收說明內容識別碼之 UINT 的位址。 如果是 Null，則不會傳回任何識別碼。

### <a name="return-value"></a>傳回值

如果函式成功，則為非零;否則，如果沒有可用的錯誤訊息正文，則為0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [CException：： GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[例外狀況處理](../../mfc/exception-handling-in-mfc.md)
