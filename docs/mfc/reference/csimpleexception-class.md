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
ms.openlocfilehash: 8fb5f7e2133f1055cde05b2dc1358896c9ea0c20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508288"
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
|[CSimpleException::CSimpleException](#csimpleexception)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSimpleException::GetErrorMessage](#geterrormessage)|提供有關發生錯誤的文字。|

## <a name="remarks"></a>備註

`CSimpleException` 是資源關鍵 MFC 例外狀況的基底類別，並處理的擁有權和初始化的錯誤訊息。 下列類別會使用`CSimpleException`作為其基底類別：

|||
|-|-|
|[CMemoryException 類別](../../mfc/reference/cmemoryexception-class.md)|記憶體不足例外狀況|
|[CNotSupportedException 類別](../../mfc/reference/cnotsupportedexception-class.md)|不支援的作業要求|
|[CResourceException 類別](../../mfc/reference/cresourceexception-class.md)|找不到或無法建立的 Windows 資源|
|[CUserException 類別](../../mfc/reference/cuserexception-class.md)|找不到例外狀況，指出資源|
|[CInvalidArgException 類別](../../mfc/reference/cinvalidargexception-class.md)|表示無效的引數的例外狀況|

因為`CSimpleException`是抽象的基底類別，您不能宣告`CSimpleException`直接物件。 相反地，您必須宣告衍生的物件，例如在上表中的物件。 如果您宣告衍生的類別，使用先前的類別做為模型。

如需詳細資訊，請參閱 < [CException 類別](../../mfc/reference/cexception-class.md)主題並[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="csimpleexception"></a>  CSimpleException::CSimpleException

建構函式。

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>參數

*bAutoDelete*<br/>
指定 TRUE，如果記憶體`CSimpleException`已在堆積上配置物件。 這會導致`CSimpleException`物件時刪除`Delete`呼叫成員函式可刪除例外狀況。 如果指定 FALSE`CSimpleException`物件在堆疊上，或為全域物件。 在此情況下，`CSimpleException`物件將不會刪除`Delete`呼叫成員函式。

### <a name="remarks"></a>備註

您通常不需要直接呼叫這個建構函式。 擲回例外狀況的函式應該建立的執行個體`CException`-衍生的類別並呼叫其建構函式，則應該使用下列其中一個 MFC 擲回函式，例如[AfxThrowFileException](exception-processing.md#afxthrowfileexception)擲回預先定義的類型。

##  <a name="geterrormessage"></a>  CSimpleException::GetErrorMessage

呼叫此成員函式，來提供有關發生錯誤的文字。

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>參數

*lpszError*<br/>
將會收到一則錯誤訊息的緩衝區指標。

*nMaxError*<br/>
最大緩衝區可以保存，包括 NULL 結束字元的字元數。

*pnHelpContext*<br/>
將會收到說明內容識別碼。 UINT 的地址 如果是 NULL，則會不傳回任何識別碼。

### <a name="return-value"></a>傳回值

如果成功，函式，非零值。否則為 0，如果沒有任何錯誤訊息文字使用。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [CException::GetErrorMessage](../../mfc/reference/cfileexception-class.md#geterrormessage)。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[例外狀況處理](../../mfc/exception-handling-in-mfc.md)

