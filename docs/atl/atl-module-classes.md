---
title: ATL 模組類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 777d81fbe1de48289863fda00591a5328b40cf4c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="atl-module-classes"></a>ATL 模組類別
本主題討論了新 ATL 7.0 中的模組類別。  
  
## <a name="ccommodule-replacement-classes"></a>CComModule 取代類別  
 使用 ATL 舊版`CComModule`。 ATL 7.0 中`CComModule`功能由數個類別取代：  
  
-   [CAtlBaseModule](../atl/reference/catlbasemodule-class.md)包含大部分使用 ATL 的應用程式所需的資訊 包含 HINSTANCE 的模組和資源執行個體。  
  
-   [CAtlComModule](../atl/reference/catlcommodule-class.md)包含 ATL 中的 COM 類別所需的資訊  
  
-   [CAtlWinModule](../atl/reference/catlwinmodule-class.md)包含所需的 ATL 中的視窗類別資訊  
  
-   [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md)包含支援偵錯介面。  
  
-   [CAtlModule](../atl/reference/catlmodule-class.md)下列`CAtlModule`-自訂衍生的類別中的特定應用程式類型所需的資訊。 這些類別中的大部分成員會覆寫：  
  
    -   [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) DLL 應用程式中使用。 提供標準的匯出程式碼。  
  
    -   [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) EXE 應用程式中使用。 提供 EXE 中所需的程式碼。  
  
    -   [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md)提供建立 Windows NT 和 Windows 2000 服務的支援。  
  
 `CComModule` 回溯相容性仍可使用。  
  
## <a name="reasons-for-distributing-ccommodule-functionality"></a>散發 CComModule 功能的原因  
 功能`CComModule`已散發到數個新的類別，原因如下：  
  
-   進行中的功能`CComModule`精細。  
  
     在另外的類別現已支援的 COM、 視窗化、 偵錯介面，和應用程式專屬 （DLL 或 EXE） 的功能。  
  
-   自動宣告每一個這些模組的全域執行的個體。  
  
     要求的模組類別的全域執行個體連結至專案中。  
  
-   移除您不再需要呼叫 Init 和詞彙的方法。  
  
     Init 和詞彙方法都移到建構函式和解構函式的模組類別;此外已不再需要呼叫 Init 和詞彙。  
  
## <a name="see-also"></a>另請參閱  
 [概念](../atl/active-template-library-atl-concepts.md)   
 [類別概觀](../atl/atl-class-overview.md)

