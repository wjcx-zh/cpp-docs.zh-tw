---
title: ATL 服務 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- CServiceModule
dev_langs:
- C++
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db13b443e605168389f0a9bc767ba29a75d4234d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="atl-services"></a>ATL 服務
若要建立您的 ATL COM 物件，使其在服務中執行，只是服務 (EXE) 從清單中選取的伺服器選項，ATL 專案精靈 中。 精靈接著會建立一個衍生自類別`CAtlServiceModuleT`實作服務。  
  
 ATL COM 物件建立時為服務，它只會登錄為本機伺服器，而且它不會出現在 [控制台] 中的服務清單。 這是因為它是做為服務比本機伺服器為服務偵錯更容易。 若要安裝為服務，請在命令提示字元執行下列命令：  
  
 `YourEXE` `.exe /Service`  
  
 若要解除安裝它，請執行下列命令：  
  
 `YourEXE` `.exe /UnregServer`  
  
 本節中的前四個主題將討論的執行期間所發生的動作`CAtlServiceModuleT`成員函式。 這些主題出現的相同順序通常稱為函式。 若要改善了解這些主題，最好使用 ATL 專案精靈，做為參考所產生的原始程式碼。 這些前四個主題包括：  
  

-   [CAtlServiceModuleT::Start 函式](../atl/reference/catlservicemodulet-class.md#start)  
  
-   [CAtlServiceModuleT::ServiceMain 函式](../atl/reference/catlservicemodulet-class.md#servicemain)  
  
-   [CAtlServiceModuleT::Run 函式](../atl/reference/catlservicemodulet-class.md#run)  
  
-   [CAtlServiceModuleT::Handler 函式](../atl/reference/catlservicemodulet-class.md#handler)  
  
 最後三個主題會討論與開發服務相關的概念：  
  
-   [登錄項目](../atl/registry-entries.md)ATL 服務  
  
-   [DCOMCNFG](../atl/dcomcnfg.md)  
  
-   [偵錯提示](../atl/debugging-tips.md)ATL 服務  
  
## <a name="see-also"></a>另請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)

