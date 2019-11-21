---
title: 例外狀況：OLE 例外狀況
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
ms.openlocfilehash: 1606a0f5a86996345e12024cf6416afdf6bdc82b
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246701"
---
# <a name="exceptions-ole-exceptions"></a>例外狀況：OLE 例外狀況

在 OLE 中處理例外狀況所用的技術和設備，與處理其他例外狀況的技術和設備相同。 For further information on exception handling, see the article [Modern C++ best practices for exceptions and error handling](../cpp/errors-and-exception-handling-modern-cpp.md).

所有例外狀況物件皆衍生自抽象基底類別 `CException`。 MFC 提供處理 OLE 例外狀況的兩種類別：

- [COleException](../mfc/reference/coleexception-class.md) For handling general OLE exceptions.

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) For generating and handling OLE dispatch (automation) exceptions.

這兩個類別之間的差異在提供的資訊量及其用途。 `COleException` 具有包含例外狀況之 OLE 狀態碼的公用資料成員。 `COleDispatchException` 提供更多資訊，包括下列：

- 應用程式專屬的錯誤碼

- 錯誤描述，例如「磁碟已滿」

- 您的應用程式可用來為使用者提供額外資訊的說明內容

- 您的應用程式的說明檔名稱

- 造成例外狀況之應用程式的名稱

`COleDispatchException` 提供更多資訊，以便與 Microsoft Visual Basic 這類的產品搭配使用。 口頭錯誤描述可用於訊息方塊或其他通知，說明資訊則可用來協助使用者回應造成例外狀況的情況。

Two global functions correspond to the two OLE exception classes: [AfxThrowOleException](../mfc/reference/exception-processing.md#afxthrowoleexception) and [AfxThrowOleDispatchException](../mfc/reference/exception-processing.md#afxthrowoledispatchexception). 使用它們分別擲回一般 OLE 例外狀況和 OLE 分派例外狀況。

## <a name="see-also"></a>請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)
