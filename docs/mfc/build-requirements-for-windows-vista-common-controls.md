---
title: Windows 通用控制項的組建需求
ms.date: 08/19/2019
helpviewer_keywords:
- Common Controls (MFC), build requirements
- Common Controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
ms.openlocfilehash: cf2139e04d2f72feb7951010caa351d67ccc5a93
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619747"
---
# <a name="build-requirements-for-windows-common-controls"></a>Windows 通用控制項的組建需求

Microsoft Foundation Class （MFC）程式庫支援[Windows 通用控制項](/windows/win32/controls/common-controls-intro)。 通用控制項包含在 Windows 中，而程式庫則包含在 Visual Studio 中。 MFC 程式庫提供新的方法，可增強現有的類別，以及其他支援 Windows 通用控制項的類別和方法。 當您建置應用程式時，您應該遵循下列章節中描述的編譯和移轉需求。

## <a name="compilation-requirements"></a>編譯需求

### <a name="supported-versions"></a>支援的版本

MFC 支援所有版本的通用控制項。 如需 Windows 通用控制項版本的相關資訊，請參閱[通用控制項版本](/windows/win32/controls/common-control-versions)。

### <a name="supported-character-sets"></a>支援的字元集。

Windows 通用控制項僅支援 Unicode 字元集，而非 ANSI 字元集。 如果您已在命令列建置應用程式，請使用下列二者定義 (/D) 編譯器選項，以指定 Unicode 做為基底字元集：

```
/D_UNICODE /DUNICODE
```

如果您在 Visual Studio 整合式開發環境（IDE）中建立應用程式，請在專案屬性的 [**一般**] 節點中，指定 [**字元集**] 屬性的 [ **Unicode 字元集**] 選項。

## <a name="migration-requirements"></a>移轉需求

如果您使用 Visual Studio IDE 來建立使用 Windows 通用控制項的新 MFC 應用程式，IDE 會自動宣告適當的資訊清單。 不過，如果您將現有的 MFC 應用程式從 Visual Studio 2005 或更早版本遷移，而且想要使用通用控制項，則 IDE 不會自動提供資訊清單資訊來升級您的應用程式。 相反地，您必須在先行編譯標頭檔中手動插入下列原始程式碼：

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

[一般 MFC 主題](general-mfc-topics.md)<br/>
[階層架構圖表](hierarchy-chart.md)<br/>
[已被取代的 ANSI API](deprecated-ansi-apis.md)
