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
ms.openlocfilehash: 71b17e777db9d6351192da7cffd075b3a64553bd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222923"
---
# <a name="cmemoryexception-class"></a>CMemoryException 類別

表示記憶體不足例外狀況。

## <a name="syntax"></a>語法

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CMemoryException：： CMemoryException](#cmemoryexception)|建構 `CMemoryException` 物件。|

## <a name="remarks"></a>備註

不需要進一步的資格或可能。 會自動擲回記憶體例外狀況 **`new`** 。 例如，如果您使用來撰寫自己的記憶體函式，則 `malloc` 您會負責擲回記憶體例外狀況。

如需的詳細資訊 `CMemoryException` ，請參閱[例外狀況處理（MFC）](../../mfc/exception-handling-in-mfc.md)一文。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>需求

**標頭：** afx。h

## <a name="cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a>CMemoryException：： CMemoryException

建構 `CMemoryException` 物件。

```
CMemoryException();
```

### <a name="remarks"></a>備註

請勿直接使用此函式，而是呼叫全域函式[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)。 這個全域函式可能會在記憶體不足的情況下成功，因為它會在先前配置的記憶體中建立例外狀況物件。 如需例外狀況處理的詳細資訊，請參閱[例外](../exception-handling-in-mfc.md)狀況。

## <a name="see-also"></a>另請參閱

[CException 類別](cexception-class.md)<br/>
[階層架構圖表](../hierarchy-chart.md)
