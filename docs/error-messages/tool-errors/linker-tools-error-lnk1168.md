---
title: 連結器工具錯誤 LNK1168 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1168
dev_langs:
- C++
helpviewer_keywords:
- LNK1168
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a80aa365edf3e39c41ed73d815cc82de6ce9a52
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118163"
---
# <a name="linker-tools-error-lnk1168"></a>連結器工具錯誤 LNK1168

無法開啟 filename 以寫入資料

連結器無法寫入 `filename`。 另一個程序可能正在使用檔案並且將檔案控制代碼鎖定，或是您沒有檔案或檔案所在目錄或網路共用的寫入權限。 此錯誤通常發生暫時性的狀況 — 例如，防毒程式，所保留的鎖定檔案搜尋索引的程序，或 Visual Studio 建置系統所持有的延遲釋放鎖定。

若要修正此問題，請確認 `filename` 檔案控制代碼未鎖定，而且您擁有檔案的寫入權限。 如果檔案是可執行檔，請確認檔案尚未執行。

您可以使用 Windows SysInternals 公用程式[處理](http://technet.microsoft.com/sysinternals/bb896655.aspx)或是[Process Explorer](http://technet.microsoft.com/sysinternals/bb896653)若要判斷哪個處理序擁有檔案控制代碼上的鎖定`filename`。 您也可以使用 Process Explorer 釋放開放檔案控制代碼的鎖定。 如需如何使用這些公用程式的詳細資訊，請參閱公用程式隨附的說明檔。

如果檔案是由防毒程式鎖定，您可以將組建輸出目錄從防毒程式的自動掃描範圍中排除，藉以修正此問題。 防毒掃描程式通常是由檔案系統中建立的新檔案觸發，掃描程式會將檔案鎖定，同時讓掃描繼續進行。 請參閱防毒程式文件中關於如何將特定目錄從掃描範圍中排除的詳細資訊。

如果檔案已由搜尋索引服務鎖定，您可以將組建輸出目錄從自動索引範圍中排除，藉以修正這個問題。 如需詳細資訊，請參閱索引服務相關文件。 若要變更 Windows 搜尋索引服務，請使用**編製索引的選項**在 Windows 中**控制台**。 如需詳細資訊，請參閱 <<c0> [ 使用索引會改善 Windows 搜尋： 常見問題集](http://windows.microsoft.com/en-us/windows/improve-windows-searches-using-index-faq#1TC=windows-7)。

如果您的可執行檔無法由建置流程覆寫，則可能是被 [檔案總管] 鎖定。 如果**應用程式體驗**服務已停用，檔案總管可能要抓緊頭上的可執行檔的檔案控制代碼鎖定時間較長。 若要修正此問題，請執行**services.msc** ，然後開啟**屬性**對話方塊**應用程式體驗**服務。 變更**啟動類型**從**停用**來**手動**。

## <a name="see-also"></a>另請參閱

[您當您嘗試建置方案或 ActiveX 專案在 Visual c + + 時可能會收到 「 錯誤 PRJ0008 」 或 「 嚴重錯誤 LNK1168 」 錯誤訊息](http://support.microsoft.com/kb/308358)