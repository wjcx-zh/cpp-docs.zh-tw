---
title: CMemoryException 類別
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: 375b4227a25ae4c18cfd263eff4c3ec13f1304e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369999"
---
# <a name="cmemoryexception-class"></a>CMemoryException 類別

表示記憶體不足例外狀況。

## <a name="syntax"></a>語法

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[記憶體例外::C記憶體異常](#cmemoryexception)|建構 `CMemoryException` 物件。|

## <a name="remarks"></a>備註

沒有必要或可能進一步的資格。 記憶體異常由**新**自動引發。 例如,`malloc`如果您編寫自己的記憶體函數,則負責引發記憶體異常。

有關的詳細資訊`CMemoryException`,請參閱文章[異常處理 (MFC)。](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>需求

**標題:** afx.h

## <a name="cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a>記憶體例外::C記憶體異常

建構 `CMemoryException` 物件。

```
CMemoryException();
```

### <a name="remarks"></a>備註

不要直接使用此建構函數,而是調用全域函數[AfxThrowMemoryexception](exception-processing.md#afxthrowmemoryexception)。 此全域函數可以在記憶體不足的情況下成功,因為它在以前分配的記憶體中構造異常物件。 有關異常處理的詳細資訊,請參閱文章[異常](../exception-handling-in-mfc.md)。

## <a name="see-also"></a>另請參閱

[CException 類別](cexception-class.md)<br/>
[階層架構圖表](../hierarchy-chart.md)
