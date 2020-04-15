---
title: CInvalidArgException 類別
ms.date: 11/04/2016
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
ms.openlocfilehash: b28b6e84043b85a8117694a67ff5fff13e7c786b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372368"
---
# <a name="cinvalidargexception-class"></a>CInvalidArgException 類別

這個類別表示無效引數例外狀況。

## <a name="syntax"></a>語法

```
class CInvalidArgException : public CSimpleException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CInvalidArg例外:CInvalidArg例外](#cinvalidargexception)|建構函式。|

## <a name="remarks"></a>備註

物件`CInvalidArgException`表示無效的參數異常條件。

有關異常處理的詳細資訊,請參閱[「例外類](../../mfc/reference/cexception-class.md)」主題和[異常處理 (MFC)。](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="cinvalidargexceptioncinvalidargexception"></a><a name="cinvalidargexception"></a>CInvalidArg例外:CInvalidArg例外

建構函式。

```
CInvalidArgException();
```

### <a name="remarks"></a>備註

不要直接使用此構造函數;呼叫全域函數**AfxThrow 無效點異常**。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[C簡單例外類別](../../mfc/reference/csimpleexception-class.md)
