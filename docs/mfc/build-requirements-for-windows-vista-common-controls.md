---
title: Windows Vista 通用控制項的組建需求 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- common controls (MFC), build requirements
- common controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8d3e5c8cd6b4a0876d0cac8e1fb3c7e87eed9cc
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42545765"
---
# <a name="build-requirements-for-windows-vista-common-controls"></a>Windows Vista 通用控制項的組建需求
Microsoft Foundation Class (MFC) 程式庫支援 Windows 通用控制項 6.1 版。 Windows Vista 中包含的通用控制項和程式庫包含在 Visual Studio SDK。 程式庫提供增強現有的類別，以及新的類別的新方法和支援 Windows Vista 通用控制項的方法。 當您建置應用程式時，您應該遵循下列章節中描述的編譯和移轉需求。  
  
## <a name="compilation-requirements"></a>編譯需求  
  
### <a name="supported-versions"></a>支援的版本  
 一些新的類別和方法支援只有 Windows Vista 和更新版本中，而其他方法也支援舊版作業系統。 附註`Requirements`區段的每個方法主題可讓您指定的最小必要作業系統是 Windows Vista。  
  
 即使您的電腦未執行 Windows Vista，您可以建置 MFC 應用程式將您的 Windows Vista 上執行，如果您有 6.1 版 MFC 標頭檔，在您的電腦上。 不過，專為 Windows Vista 通用控制項只能在該系統上運作，而且會忽略先前的作業系統。  
  
### <a name="supported-character-sets"></a>支援的字元集。  
 新的 Windows 通用控制項僅支援 Unicode 字元集，而非 ANSI 字元集。 如果您已在命令列建置應用程式，請使用下列二者定義 (/D) 編譯器選項，以指定 Unicode 做為基底字元集：  
  
```  
/D_UNICODE /DUNICODE  
```  
  
 如果您要建置您的應用程式，Visual Studio 整合式的開發環境 (IDE) 中，指定**Unicode 字元集**選項**字元集**中的屬性**一般**專案屬性的節點。  
  
 從 Windows 通用控制項 6.1 版開始，ANSI 版本的幾個 MFC 方法已被取代。 如需詳細資訊，請參閱 <<c0> [ 已被取代的 ANSI Api](../mfc/deprecated-ansi-apis.md)。  
  
## <a name="migration-requirements"></a>移轉需求  
 如果您使用 Visual Studio IDE 建置使用 Windows 通用控制項 6.1 版的新 MFC 應用程式，IDE 會自動宣告適當的資訊清單。 不過，如果您移轉舊版 Visual Studio 的現有的 MFC 應用程式，而且想要使用新的通用控制項，IDE 不會自動提供資訊清單資訊來升級您的應用程式。 相反地，您必須手動插入下列程式碼置於您**stdafx.h**檔案：  
  
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
  
## <a name="see-also"></a>另請參閱  
 [一般 MFC 主題](../mfc/general-mfc-topics.md)   
 [階層架構圖表](../mfc/hierarchy-chart.md)   
 [已被取代的 ANSI API](../mfc/deprecated-ansi-apis.md)

