---
title: 如何： 在編譯時期包含資源 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
dev_langs:
- C++
helpviewer_keywords:
- compiling source code, including resources
- comments [C++], compiled files
- resources [Visual Studio], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 856d448b096910c322750eccc7447689b08b328e
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571332"
---
# <a name="how-to-include-resources-at-compile-time"></a>如何：在編譯時期包含資源
通常可簡單且容易使用一個資源指令碼 (.rc) 檔中所有資源的預設排列方式。 不過，您可以將資源其他檔案中加入目前的專案在編譯時期藉由列出在**編譯時間指示詞**方塊中[資源包含對話方塊](../windows/resource-includes-dialog-box.md)。  
  
 有幾個原因會在主要.rc 檔以外的檔案中放置資源：  
  
-   為了將註解新增至儲存 .rc 檔時不會刪除的資源陳述式。  
  
     資源編輯器不會直接讀取.rc 或 resource.h 檔。 資源編譯器會將它們編譯成 .aps 檔，以供資源編輯器使用。 此檔案是一個編譯步驟，只會儲存符號資料。 如同正常的編譯程序一般，編譯程序期間會捨棄非符號的資訊 (例如註解)。 每當 .aps 檔未與 .rc 檔同步時，就會重新產生 .rc 檔 (例如，當您儲存時，資源編輯器會覆寫 .rc 檔和 resource.h 檔)。 資源本身的任何變更都會繼續合併在 .rc 檔中，但當 .rc 檔被覆寫後，註解就會永遠遺失。  
  
-   為了包含已開發及測試、而且不需要進一步修改的資源。 (資源編輯器無法編輯不含 .rc 副檔名的任何加入的檔案。)  
  
-   為了包含數個不同的專案正在使用的資源，或屬於原始程式碼版本控制系統的資源，因而必須存在中央位置，讓修改影響所有專案。  
  
-   為了包含自訂格式的資源 (例如 RCDATA 資源)。 RCDATA 資源可能會有特殊需求。 例如，您無法將運算式做為 nameID 欄位的值。 如需詳細資訊，請參閱 [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] 文件。  
  
 如果您將區段在現有的.rc 檔符合下列任一條件時，您應該將該區段置於一或多個個別.rc 檔，並將它們包含在專案中使用[資源包含對話方塊](../windows/resource-includes-dialog-box.md)。 *Projectname*.rc2 檔建立新專案的 \res 子目錄中用於此目的。  
  
### <a name="to-include-resources-in-your-project-at-compile-time"></a>在編譯時期，於專案中包含資源  
  
1.  將資源放在包含唯一檔案名稱的資源指令碼檔案。 請勿使用*projectname*.rc，因為這是用於主要資源指令碼檔案的檔案名稱。  
  
2.  以滑鼠右鍵按一下.rc 檔 (在[資源檢視](../windows/resource-view-window.md))，然後選擇**Resource Includes**從捷徑功能表。  
  
3.  在 **編譯時間指示詞**方塊中，加入[#include](../preprocessor/hash-include-directive-c-cpp.md)編譯器指示詞，以在開發環境中的主要資源檔中納入新的資源檔。  
  
     以這種方式包含的檔案中資源，都會在編譯時期成為可執行檔的一部分。 當您在專案的主要 .rc 檔上工作時，無法直接編輯或修改它們。 您需要個別開啟包含的 .rc 檔。 資源編輯器無法編輯不含 .rc 副檔名的任何加入的檔案。  
  
## <a name="requirements"></a>需求  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [資源檔](../windows/resource-files-visual-studio.md)   
 [資源編輯器](../windows/resource-editors.md)