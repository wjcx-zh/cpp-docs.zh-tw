---
title: "Windows Vista 通用控制項的組建需求 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- common controls (MFC), build requirements
- common controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76919bcdd416ed7195e94ed1fa0b2e3f3a4d573d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="build-requirements-for-windows-vista-common-controls"></a>Windows Vista 通用控制項的組建需求
Microsoft Foundation Class (MFC) 程式庫支援 Windows 通用控制項 6.1 版。 通用控制項包含在 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] 中，而程式庫則包含在 [!INCLUDE[vsipsdk](../mfc/includes/vsipsdk_md.md)] 中。 程式庫會提供新的方法，以增強現有類別，以及新的類別和方法，可支援[!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]通用控制項。 當您建置應用程式時，您應該遵循下列章節中描述的編譯和移轉需求。  
  
## <a name="compilation-requirements"></a>編譯需求  
  
### <a name="supported-versions"></a>支援的版本  
 雖然其他方法也支援舊版的作業系統，但是一些新的類別和方法只支援 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] 和更新版本。 在每個方法主題的 `Requirements` 區段的附註，指定何時需要以 [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)] 作為最低作業系統。  
  
 即使您的電腦不會執行[!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]，您可以建置 MFC 應用程式上執行[!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]有 6.1 版 MFC 標頭檔，在您的電腦上。 不過，通用控制項專為[!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)]只能在該系統上運作，而且會忽略由舊版作業系統。  
  
### <a name="supported-character-sets"></a>支援的字元集。  
 新的 Windows 通用控制項僅支援 Unicode 字元集，而非 ANSI 字元集。 如果您已在命令列建置應用程式，請使用下列二者定義 (/D) 編譯器選項，以指定 Unicode 做為基底字元集：  
  
```  
/D_UNICODE /DUNICODE  
```  
  
 如果您建置您的應用程式，Visual Studio 整合式的開發環境 (IDE) 中，指定**Unicode 字元集**選項**字元集**屬性**一般**專案屬性的節點。  
  
 從 Windows 通用控制項 6.1 版開始，ANSI 版本的幾個 MFC 方法已被取代。 如需詳細資訊，請參閱[已被取代的 ANSI Api](../mfc/deprecated-ansi-apis.md)。  
  
## <a name="migration-requirements"></a>移轉需求  
 如果您使用 Visual Studio IDE 建置使用 Windows 通用控制項 6.1 版的新 MFC 應用程式，IDE 會自動宣告適當的資訊清單。 不過，如果您移轉舊版 Visual Studio 的現有的 MFC 應用程式，而且想要使用新的通用控制項，IDE 不會自動提供資訊清單資訊來升級您的應用程式。 您必須改為在 stdafx.h 檔案中手動插入下列原始程式碼：  
  
```  
#ifdef UNICODE  
#if defined _M_IX86  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='x86' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#elif defined _M_IA64  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='ia64' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#elif defined _M_X64  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='amd64' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#else  
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='*' publicKeyToken='6595b64144ccf1df' language='*'\"")  
#endif  
#endif  
```  
  
## <a name="see-also"></a>請參閱  
 [一般 MFC 主題](../mfc/general-mfc-topics.md)   
 [階層架構圖表](../mfc/hierarchy-chart.md)   
 [已被取代的 ANSI API](../mfc/deprecated-ansi-apis.md)

