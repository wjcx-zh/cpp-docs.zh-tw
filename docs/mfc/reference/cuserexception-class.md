---
title: CUserException 類別
ms.date: 11/04/2016
f1_keywords:
- CUserException
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
ms.openlocfilehash: 72d8537616792859a2b00a1a5cd880ce5eb452bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323433"
---
# <a name="cuserexception-class"></a>CUserException 類別

擲回以停止使用者作業。

## <a name="syntax"></a>語法

```
class CUserException : public CSimpleException
```

## <a name="remarks"></a>備註

使用`CUserException`當您想要用於應用程式特定例外狀況的擲回/catch 例外狀況機制。 「 使用者 」 中的類別名稱可以解譯為 「 我的使用者做例外，需要處理的項目。 」

A`CUserException`通常會呼叫全域函式之後擲回`AfxMessageBox`來通知使用者作業已失敗。 當您撰寫例外狀況處理常式時，請特別因為使用者通常已經已通知的失敗時，才處理例外狀況。 此架構會在某些情況下，擲回這個例外狀況。 擲回`CUserException`，警示使用者，並接著呼叫全域函式`AfxThrowUserException`。

在下列範例中，包含可能會失敗的作業的函式會警示使用者，並擲回`CUserException`。 呼叫的函式攔截到例外狀況，並特別將加以處理：

[!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]

如需有關使用`CUserException`，請參閱文章[例外狀況處理 (MFC)](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CUserException`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CException 類別](../../mfc/reference/cexception-class.md)
