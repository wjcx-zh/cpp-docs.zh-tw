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
ms.openlocfilehash: b29112b4901a1fecac37aa7ae61496e874959370
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372189"
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
|[CResourceException::CResourceException](#cresourceexception)|建構 `CResourceException` 物件。|

## <a name="remarks"></a>備註

沒有進一步限定性條件是必要或不可能。

如需有關使用`CResourceException`，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cresourceexception"></a>  CResourceException::CResourceException

建構 `CResourceException` 物件。

```
CResourceException();
```

### <a name="remarks"></a>備註

請勿直接使用這個建構函式，但而不是呼叫全域函式[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)。 如需例外狀況的詳細資訊，請參閱文章[MFC 的例外狀況處理](../exception-handling-in-mfc.md)。

## <a name="see-also"></a>另請參閱

[CException 類別](cexception-class.md)<br/>
[階層架構圖表](../hierarchy-chart.md)
