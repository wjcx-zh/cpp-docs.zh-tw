---
title: 專案建置警告 PRJ0049 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8df6fcb8bc5d6517a46279e0bef5036db1e81241
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-warning-prj0049"></a>專案建置警告 PRJ0049
參考的目標 '\<參考 >' 需要.NET Framework \<m >，此專案的目標 framework 執行將會失敗  
  
 使用 Visual Studio 2008 建立的應用程式可以指定的版本[!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)]它們應將目標設。 如果您將參考加入組件或專案的版本而定，[!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)]比目標版本還新，就會在編譯時期這個警告。  
  
### <a name="to-correct-this-warning"></a>若要更正這個警告  
  
1.  選擇下列其中一項：  
  
    -   變更在專案的目標的 framework**屬性頁**對話方塊，讓它位於晚於或等於所有參考的組件和專案的最小 framework 版本。 如需詳細資訊，請參閱[將參考加入](../../ide/adding-references-in-visual-cpp-projects.md)。  
  
    -   移除參考的組件或具有晚於目標 framework 的最小 framework 版本的專案。 這些項目將會標示警告圖示，在專案的**屬性頁**。  
  
## <a name="see-also"></a>另請參閱  
 [專案建置錯誤和警告 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)