---
title: C簡單例外類別
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
ms.openlocfilehash: eb94ba9e3d26b3cd910f23c3d4abb29d3b8b1cd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318355"
---
# <a name="csimpleexception-class"></a>C簡單例外類別

這個類別是資源關鍵 MFC 例外狀況的基底類別。

## <a name="syntax"></a>語法

```
class AFX_NOVTABLE CSimpleException : public CException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[簡單例外::簡單例外](#csimpleexception)|建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[簡單例外:取得錯誤訊息](#geterrormessage)|提供有關已發生錯誤的文本。|

## <a name="remarks"></a>備註

`CSimpleException`是資源關鍵型 MFC 異常的基本類,並處理錯誤消息的擁有權和初始化。 以下類別用作`CSimpleException`其基類:

|||
|-|-|
|[CMemoryException 類別](../../mfc/reference/cmemoryexception-class.md)|記憶體不足異常|
|[CNotSupportedException 類別](../../mfc/reference/cnotsupportedexception-class.md)|要求不支援的作業|
|[CResourceException 類別](../../mfc/reference/cresourceexception-class.md)|找不到或無法建立的視窗資源|
|[CUserException 類別](../../mfc/reference/cuserexception-class.md)|指示找不到資源的例外|
|[CInvalidArgException 類別](../../mfc/reference/cinvalidargexception-class.md)|指示無效參數的例外|

因為`CSimpleException`是抽象基類,因此不能直接`CSimpleException`聲明 物件。 相反,必須聲明派生物件,如上表中的物件。 如果要聲明自己的派生類,請使用前面的類作為模型。

有關詳細資訊,請參閱[「例外類」](../../mfc/reference/cexception-class.md)主題和[異常處理 (MFC)。](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`CSimpleException`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="csimpleexceptioncsimpleexception"></a><a name="csimpleexception"></a>簡單例外::簡單例外

建構函式。

```
CSimpleException();
explicit CSimpleException(BOOL bAutoDelete);
```

### <a name="parameters"></a>參數

*b 自動刪除*<br/>
如果`CSimpleException`物件的記憶體已在堆上分配,請指定 TRUE。 這將導致在`CSimpleException`調用`Delete`成員函數刪除異常時刪除物件。 如果物件位於堆`CSimpleException`棧上或是全域物件,請指定 FALSE。 在這種情況下,`CSimpleException`在呼`Delete`叫成員函數時不會刪除該物件。

### <a name="remarks"></a>備註

您通常不需要直接呼叫此建構函數。 引發異常的函數應創建`CException`派生類的實例並調用其構造函數,或者它應該使用 MFC 引發函數之一(如[AfxThrowFileexception)](exception-processing.md#afxthrowfileexception)來引發預定義類型。

## <a name="csimpleexceptiongeterrormessage"></a><a name="geterrormessage"></a>簡單例外:取得錯誤訊息

調用此成員函數以提供有關已發生的錯誤的文本。

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT  nMaxError,
    PUNIT  pnHelpContext = NULL);
```

### <a name="parameters"></a>參數

*lpsz錯誤*<br/>
指向將接收錯誤消息的緩衝區的指標。

*nMax錯誤*<br/>
緩衝區可以保留的最大字元數,包括 NULL 終止符。

*pnHelpContext*<br/>
將收到説明上下文 ID 的 UINT 的位址。 如果 NULL,則不會返回任何 ID。

### <a name="return-value"></a>傳回值

如果函數成功,則非零;否則 0 如果沒有錯誤消息文本可用。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱["例外:獲取錯誤消息](../../mfc/reference/cfileexception-class.md#geterrormessage)"。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)<br/>
[例外狀況處理](../../mfc/exception-handling-in-mfc.md)
