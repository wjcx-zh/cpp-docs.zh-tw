---
title: 連結器工具錯誤 LNK1168
ms.date: 11/04/2016
f1_keywords:
- LNK1168
helpviewer_keywords:
- LNK1168
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
ms.openlocfilehash: f0eb63c124162dbb515782bbd014c556c12de153
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450897"
---
# <a name="linker-tools-error-lnk1168"></a>連結器工具錯誤 LNK1168

無法開啟 filename 以寫入資料

連結器無法寫入 `filename`。 另一個程序可能正在使用檔案並且將檔案控制代碼鎖定，或是您沒有檔案或檔案所在目錄或網路共用的寫入權限。 此錯誤通常發生暫時性的狀況 — 例如，防毒程式，所保留的鎖定檔案搜尋索引的程序，或 Visual Studio 建置系統所持有的延遲釋放鎖定。

若要修正此問題，請確認 `filename` 檔案控制代碼未鎖定，而且您擁有檔案的寫入權限。 如果檔案是可執行檔，請確認檔案尚未執行。

您可以使用 Windows SysInternals 公用程式[處理](/sysinternals/downloads/handle)或是[Process Explorer](/sysinternals/downloads/process-explorer)若要判斷哪個處理序擁有檔案控制代碼上的鎖定`filename`。 您也可以使用 Process Explorer 釋放開放檔案控制代碼的鎖定。 如需如何使用這些公用程式的詳細資訊，請參閱公用程式隨附的說明檔。

如果檔案是由防毒程式鎖定，您可以將組建輸出目錄從防毒程式的自動掃描範圍中排除，藉以修正此問題。 防毒掃描程式通常是由檔案系統中建立的新檔案觸發，掃描程式會將檔案鎖定，同時讓掃描繼續進行。 請參閱防毒程式文件中關於如何將特定目錄從掃描範圍中排除的詳細資訊。

如果檔案已由搜尋索引服務鎖定，您可以將組建輸出目錄從自動索引範圍中排除，藉以修正這個問題。 如需詳細資訊，請參閱索引服務相關文件。 若要變更 Windows 搜尋索引服務，請使用**編製索引的選項**在 Windows 中**控制台**。 如需詳細資訊，請參閱[搜尋 Windows 10 中編製索引：常見問題集](https://support.microsoft.com/help/4098843/windows-10-search-indexing-faq)。

如果您的可執行檔無法由建置流程覆寫，則可能是被 [檔案總管] 鎖定。 如果**應用程式體驗**服務已停用，檔案總管可能要抓緊頭上的可執行檔的檔案控制代碼鎖定時間較長。 若要修正此問題，請執行**services.msc** ，然後開啟**屬性**對話方塊**應用程式體驗**服務。 變更**啟動類型**從**停用**來**手動**。
