---
title: ATL 服務
ms.date: 11/04/2016
f1_keywords:
- CServiceModule
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
ms.openlocfilehash: 50a3eecf210cacc35cd80ad82da079b18c998c8b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456104"
---
# <a name="atl-services"></a>ATL 服務

若要使其在服務中執行，請建立您的 ATL COM 物件，直接從 [ATL 專案精靈] 中的 [伺服器] 選項的清單選取服務 (EXE)。 精靈接著會建立一個衍生自類別`CAtlServiceModuleT`實作服務。

ATL COM 物件建立時即服務，它只會註冊為本機伺服器，和它不會出現在 [控制台] 中的服務清單。 這是因為它是比做為服務的本機伺服器作為服務進行偵錯的工作變得更容易。 若要將它安裝為服務，在命令提示字元執行下列命令：

`YourEXE` `.exe /Service`

若要解除安裝它，請執行下列命令：

`YourEXE` `.exe /UnregServer`

在本節中的前四個主題將討論在執行期間發生的動作`CAtlServiceModuleT`成員函式。 為一般呼叫的函式，這些主題會出現在相同的順序。 若要改善您對這些主題的瞭解，最好使用 ATL 專案精靈，做為參考所產生的原始程式碼。 這些前四個主題包括：

- [Catlservicemodulet:: Start 函式](../atl/reference/catlservicemodulet-class.md#start)

- [Catlservicemodulet:: Servicemain 函式](../atl/reference/catlservicemodulet-class.md#servicemain)

- [Catlservicemodulet:: Run 函式](../atl/reference/catlservicemodulet-class.md#run)

- [Catlservicemodulet:: Handler 函式](../atl/reference/catlservicemodulet-class.md#handler)

最後三個主題將討論開發之服務的相關概念：

- [登錄項目](../atl/registry-entries.md)ATL 服務

- [DCOMCNFG](../atl/dcomcnfg.md)

- [偵錯秘訣](../atl/debugging-tips.md)ATL 服務

## <a name="see-also"></a>另請參閱

[概念](../atl/active-template-library-atl-concepts.md)

