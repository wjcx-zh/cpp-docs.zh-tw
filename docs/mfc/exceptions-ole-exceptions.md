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
ms.openlocfilehash: 7bd0b0cb2c9eb6fe49356ae8fd4602676d54fa66
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622779"
---
# <a name="exceptions-ole-exceptions"></a>例外狀況：OLE 例外狀況

在 OLE 中處理例外狀況所用的技術和設備，與處理其他例外狀況的技術和設備相同。 如需例外狀況處理的進一步資訊，請參閱[適用于例外狀況和錯誤處理的新式 c + + 最佳做法](../cpp/errors-and-exception-handling-modern-cpp.md)一文。

所有例外狀況物件皆衍生自抽象基底類別 `CException`。 MFC 提供處理 OLE 例外狀況的兩種類別：

- [COleException](reference/coleexception-class.md)用於處理一般 OLE 例外狀況。

- [COleDispatchException](reference/coledispatchexception-class.md)用於產生和處理 OLE 分派（自動化）例外狀況。

這兩個類別之間的差異在提供的資訊量及其用途。 `COleException` 具有包含例外狀況之 OLE 狀態碼的公用資料成員。 `COleDispatchException` 提供更多資訊，包括下列：

- 應用程式專屬的錯誤碼

- 錯誤描述，例如「磁碟已滿」

- 您的應用程式可用來為使用者提供額外資訊的說明內容

- 您的應用程式的說明檔名稱

- 造成例外狀況之應用程式的名稱

`COleDispatchException` 提供更多資訊，以便與 Microsoft Visual Basic 這類的產品搭配使用。 口頭錯誤描述可用於訊息方塊或其他通知，說明資訊則可用來協助使用者回應造成例外狀況的情況。

兩個全域函式對應至兩個 OLE 例外狀況類別： [AfxThrowOleException](reference/exception-processing.md#afxthrowoleexception)和[AfxThrowOleDispatchException](reference/exception-processing.md#afxthrowoledispatchexception)。 使用它們分別擲回一般 OLE 例外狀況和 OLE 分派例外狀況。

## <a name="see-also"></a>另請參閱

[例外狀況處理](exception-handling-in-mfc.md)
