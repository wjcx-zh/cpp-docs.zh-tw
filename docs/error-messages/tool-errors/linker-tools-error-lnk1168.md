---
title: "連結器工具錯誤 LNK1168 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1168
dev_langs:
- C++
helpviewer_keywords:
- LNK1168
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 12dfce4243f0872735158df7ccd81b7c6e29efc8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1168"></a>連結器工具錯誤 LNK1168
無法開啟 filename 以寫入資料  
  
 連結器無法寫入 `filename`。 另一個程序可能正在使用檔案並且將檔案控制代碼鎖定，或是您沒有檔案或檔案所在目錄或網路共用的寫入權限。 這個錯誤通常是由暫時性狀態所導致，例如防毒程式的鎖定、檔案搜尋索引程序，或者 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 建置系統所持有的鎖定延遲釋放。  
  
 若要修正此問題，請確認 `filename` 檔案控制代碼未鎖定，而且您擁有檔案的寫入權限。 如果檔案是可執行檔，請確認檔案尚未執行。  
  
 您可以使用 Windows SysInternals 公用程式[處理](http://technet.microsoft.com/sysinternals/bb896655.aspx)或[處理序總管](http://technet.microsoft.com/sysinternals/bb896653)來判斷哪些處理程序的檔案控制代碼上的鎖定`filename`。 您也可以使用 Process Explorer 釋放開放檔案控制代碼的鎖定。 如需如何使用這些公用程式的詳細資訊，請參閱公用程式隨附的說明檔。  
  
 如果檔案是由防毒程式鎖定，您可以將組建輸出目錄從防毒程式的自動掃描範圍中排除，藉以修正此問題。 防毒掃描程式通常是由檔案系統中建立的新檔案觸發，掃描程式會將檔案鎖定，同時讓掃描繼續進行。 請參閱防毒程式文件中關於如何將特定目錄從掃描範圍中排除的詳細資訊。  
  
 如果檔案已由搜尋索引服務鎖定，您可以將組建輸出目錄從自動索引範圍中排除，藉以修正這個問題。 如需詳細資訊，請參閱索引服務相關文件。 若要變更 Windows 搜尋索引服務，請使用**索引選項**windows**控制台**。 如需詳細資訊，請參閱[改善 Windows 搜尋使用的索引： 常見問題集](http://windows.microsoft.com/en-us/windows/improve-windows-searches-using-index-faq#1TC=windows-7)。  
  
 如果您的可執行檔無法由建置流程覆寫，則可能是被 [檔案總管] 鎖定。 如果**應用程式體驗**服務已停用，檔案總管可能佔用的可執行檔的檔案控制代碼鎖定一段時間。 若要修正此問題，請執行**services.msc** ，然後開啟**屬性**對話方塊的 **應用程式體驗**服務。 變更**啟動類型**從**已停用**至**手動**。  
  
## <a name="see-also"></a>請參閱  
 [您可能會收到 「 錯誤 PRJ0008 」 或 「 嚴重錯誤 LNK1168 」 錯誤訊息時您嘗試建置方案或 ActiveX 專案中 Visual c + +](http://support.microsoft.com/kb/308358)