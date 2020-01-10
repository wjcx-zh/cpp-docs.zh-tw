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

在 OLE 中處理例外狀況所用的技術和設備，與處理其他例外狀況的技術和設備相同。 如需例外狀況處理的進一步資訊，請[參閱C++例外狀況和錯誤處理的新式最佳做法](../cpp/errors-and-exception-handling-modern-cpp.md)一文。

所有例外狀況物件皆衍生自抽象基底類別 `CException`。 MFC 提供處理 OLE 例外狀況的兩種類別：

- [COleException](../mfc/reference/coleexception-class.md)用於處理一般 OLE 例外狀況。

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md)用於產生和處理 OLE 分派（自動化）例外狀況。

這兩個類別之間的差異在提供的資訊量及其用途。 `COleException` 具有公用資料成員，其中包含例外狀況的 OLE 狀態碼。 `COleDispatchException` 提供詳細資訊，包括下列各項：

- 應用程式專屬的錯誤碼

- 錯誤描述，例如「磁碟已滿」

- 您的應用程式可用來為使用者提供額外資訊的說明內容

- 您的應用程式的說明檔名稱

- 造成例外狀況之應用程式的名稱

`COleDispatchException` 提供詳細資訊，讓它可與 Microsoft Visual Basic 等產品搭配使用。 口頭錯誤描述可用於訊息方塊或其他通知，說明資訊則可用來協助使用者回應造成例外狀況的情況。

兩個全域函式對應至兩個 OLE 例外狀況類別： [AfxThrowOleException](../mfc/reference/exception-processing.md#afxthrowoleexception)和[AfxThrowOleDispatchException](../mfc/reference/exception-processing.md#afxthrowoledispatchexception)。 使用它們分別擲回一般 OLE 例外狀況和 OLE 分派例外狀況。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../mfc/exception-handling-in-mfc.md)
