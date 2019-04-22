---
title: Automation
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers, about Automation servers
- clients, Automation
- programmatic control [MFC]
- properties [MFC], Automation
- MFC, COM support
- OLE Automation
- Automation
- servers [MFC], Automation
- Automation clients
- sample applications [MFC], Automation
- methods [MFC]
- passing parameters, Automation
- Automation method [MFC]
- Automation, passing parameters
- Automation property [MFC]
- MFC COM, Automation
- methods [MFC], Automation
ms.assetid: 329117f0-c1aa-4680-a901-bfb71277dfba
ms.openlocfilehash: 7818aa708a762f2a284be029a6c3f3facd971d9a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767726"
---
# <a name="automation"></a>Automation

Automation (先前稱為 OLE Automation) 可讓應用程式操作另一個應用程式中實作的物件，或者公開物件以便提供給其他程式操作。

[Automation 伺服器](../mfc/automation-servers.md) 是一個應用程式 (為 COM 伺服器類型)，其透過 COM 介面公開其功能給其他應用程式 (稱為 [Automation 用戶端](../mfc/automation-clients.md)) 使用。 公開可讓 Automation 用戶端藉由直接存取物件並使用所提供的服務，以自動化執行某些函式。

Automation 伺服器和用戶端使用的 COM 介面一定是衍生自 `IDispatch` ，該介面會接受並傳回一組特定的資料類型，稱為 Automation 類型。 您可以自動化任何公開 Automation 介面的物件，提供可以從其他應用程式存取的方法和屬性。 Aurotmation 可供 OLE 和 COM 物件使用。 自動化物件可以是本機或遠端 (在網路的另一台電腦上進行存取)；因此 Automation 有兩類：

- Automation (區域)。

- （在網路上使用分散式 COM 或 DCOM） 遠端 Automation。

當應用程式提供可供其他應用程式使用的功能時，公開物件是有益處的。 例如，某個 ActiveX 控制項是一種 Automation 伺服器類型，此時裝載 ActiveX 控制項的應用程式即是該控制項的 Automation 用戶端。

另一個例子，文書處理器可能會公開其拼字檢查功能給其他程式。 公開物件可讓廠商藉由使用其他應用程式的現成功能來改善其應用程式。 如此一來，Automation 會在應用程式層級本身套用某些物件導向程式設計的準則 (例如重複使用性和封裝)。

更重要的是，其支援提供給使用者和方案提供者的 Automation。 透過通用、明確定義的介面公開應用程式的功能，Automation 可讓單一的一般程式語言 (如 Microsoft Visual Basic) 建立複雜的解決方案，而不需要使用應用程式專屬的巨集語言才能建立。

許多商業應用程式 (例如 Microsoft Excel 和 Microsoft Visual C++) 可讓您自動化其大部分的功能。 例如，在視覺效果C++，您可以撰寫 VBScript 巨集來自動化組建、 程式碼編輯，或偵錯工作的層面。

##  <a name="_core_passing_parameters_in_automation"></a> 在 Automation 內傳遞參數

建立 Automation 方法的其中一項困難點是，要在 Automation 伺服器和用戶端之間傳遞資料時，提供一致的「安全」機制。 Automation 使用 **VARIANT** 類型來傳遞資料。 **VARIANT** 類型是一個標記的 union。 它具有一個值的資料成員 (為匿名 C++ union) 和一個表示儲存在 union 中資訊之類型的資料成員。 **VARIANT**類型支援許多標準的資料類型：2 與 4 位元組整數、 4 和 8 位元組浮點數、 字串和布林值。 此外，它支援**HRESULT** （OLE 錯誤碼）、**貨幣**（固定點數字類型），並**日期**（絕對日期和時間） 類型，以及指標`IUnknown`和`IDispatch`介面。

**VARIANT** 類型封裝在 [COleVariant](../mfc/reference/colevariant-class.md) 類別中。 支援 **CURRENCY** 和 **DATE** 的類別封裝在 [COleCurrency](../mfc/reference/colecurrency-class.md) 和 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) 類別中。

## <a name="automation-samples"></a>Automation 範例

- [AUTOCLIK](../overview/visual-cpp-samples.md) ：使用此範例來了解 Automation 技術，可做為學習遠端 Automation 的基礎。

- [ACDUAL](../overview/visual-cpp-samples.md) ：將雙重介面加入至 Automation 伺服應用程式。

- [CALCDRIV](../overview/visual-cpp-samples.md) ：驅動 MFCCALC 的 Automation 用戶端應用程式。

- [INPROC](../overview/visual-cpp-samples.md) ：示範同處理序 Automation 伺服應用程式。

- [IPDRIVE](../overview/visual-cpp-samples.md) ：驅動 INPROC 的 Automation 用戶端應用程式。

- [MFCCALC](../overview/visual-cpp-samples.md) ：示範 Automation 用戶端應用程式。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [Automation 用戶端](../mfc/automation-clients.md)

- [Automation 伺服程式](../mfc/automation-servers.md)

- [OLE](../mfc/ole-in-mfc.md)

- [Active 技術](../mfc/mfc-com.md)

## <a name="what-do-you-want-to-do"></a>您要做什麼

- [加入 Automation 類別](../mfc/automation-servers.md)

- [使用類型程式庫](../mfc/automation-clients-using-type-libraries.md)

- [存取 Automation 伺服器](../mfc/automation-servers.md)

- [使用 C++ 撰寫 Automation 用戶端](../mfc/automation-clients.md)

## <a name="see-also"></a>另請參閱

[MFC COM](../mfc/mfc-com.md)
