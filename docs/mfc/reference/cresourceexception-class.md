---
title: CResourceException 類別
ms.date: 11/04/2016
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
ms.openlocfilehash: 557bfe1cc41c3dda65bd95d7d687820c0b9862b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368321"
---
# <a name="cresourceexception-class"></a>CResourceException 類別

當 Windows 找不到或無法配置所要求的資源時產生的。

## <a name="syntax"></a>語法

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[資源例外:C 資源例外](#cresourceexception)|建構 `CResourceException` 物件。|

## <a name="remarks"></a>備註

沒有必要或可能進一步的資格。

有關`CResourceException`使用的詳細資訊,請參閱[異常處理 (MFC) 一](../../mfc/exception-handling-in-mfc.md)文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cresourceexceptioncresourceexception"></a><a name="cresourceexception"></a>資源例外:C 資源例外

建構 `CResourceException` 物件。

```
CResourceException();
```

### <a name="remarks"></a>備註

不要直接使用此建構函數,而應呼叫全域函數[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)。 有關異常的詳細資訊,請參閱[MFC 中的異常處理](../exception-handling-in-mfc.md)一文。

## <a name="see-also"></a>另請參閱

[CException 類別](cexception-class.md)<br/>
[階層架構圖表](../hierarchy-chart.md)
