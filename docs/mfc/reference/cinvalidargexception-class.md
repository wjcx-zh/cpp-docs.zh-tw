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
ms.openlocfilehash: d2df9b482fe95ad0a13a85a51037a4cbbc28d057
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392617"
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
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|建構函式。|

## <a name="remarks"></a>備註

A`CInvalidArgException`物件表示無效的引數例外狀況。

如需有關例外狀況處理的詳細資訊，請參閱[CException 類別](../../mfc/reference/cexception-class.md)主題並[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="cinvalidargexception"></a>  CInvalidArgException::CInvalidArgException

建構函式。

```
CInvalidArgException();
```

### <a name="remarks"></a>備註

請勿直接; 使用這個建構函式呼叫全域函式**AfxThrowInvalidArgException**。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CSimpleException 類別](../../mfc/reference/csimpleexception-class.md)
