---
title: CNotSupportedException 類別
ms.date: 11/04/2016
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
ms.openlocfilehash: b859b939baef018e69b245e597eea90e608253ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363186"
---
# <a name="cnotsupportedexception-class"></a>CNotSupportedException 類別

表示因要求不支援的功能而產生的例外狀況。

## <a name="syntax"></a>語法

```
class CNotSupportedException : public CSimpleException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[不支援的例外::不支援例外](#cnotsupportedexception)|建構 `CNotSupportedException` 物件。|

## <a name="remarks"></a>備註

沒有必要或可能進一步的資格。

有關`CNotSupportedException`使用的詳細資訊,請參閱[異常處理 (MFC) 一](../../mfc/exception-handling-in-mfc.md)文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CNotSupportedException`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="cnotsupportedexceptioncnotsupportedexception"></a><a name="cnotsupportedexception"></a>不支援的例外::不支援例外

建構 `CNotSupportedException` 物件。

```
CNotSupportedException();
```

### <a name="remarks"></a>備註

不要直接使用此構造函數,而是調用全域函數[AfxThrowNot 支援異常](exception-processing.md#afxthrownotsupportedexception)。 有關異常處理的詳細資訊,請參閱[MFC 中的異常處理](../exception-handling-in-mfc.md)一文。

## <a name="see-also"></a>另請參閱

[CException 類別](cexception-class.md)<br/>
[階層架構圖表](../hierarchy-chart.md)
