---
title: 內存取版本資訊從您的程式 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.version
helpviewer_keywords:
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 18622333-d9e8-4309-9465-677cd10c79b1
ms.openlocfilehash: 028ea6126b75b914e7ff9a4ded2d08efa9d35b28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644622"
---
# <a name="accessing-version-information-from-within-your-program-c"></a>內存取版本資訊從您的程式 （c + +）

### <a name="to-access-version-information-from-within-your-program"></a>存取程式內的版本資訊

1. 如果您想要存取程式內的版本資訊，請使用 [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) 函式和 [VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) 函式。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[版本資訊編輯器](../windows/version-information-editor.md)<br/>
[版本資訊 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)