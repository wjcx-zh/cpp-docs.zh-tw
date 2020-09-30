---
title: 使用資源檔 (C++)
ms.date: 02/14/2019
helpviewer_keywords:
- resources [C++], about resources
- resources [C++], about resource files
- resource files [C++], about resource files
ms.assetid: 2699a539-b369-4b78-80f0-df03eb7b6780
ms.openlocfilehash: 3e387a1cefb6577760a34c7957d4f5019b1d49ef
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502909"
---
# <a name="working-with-resource-files"></a>使用資源檔

> [!WARNING]
> 本節適用於以 C++ 撰寫的 Windows 桌面應用程式。
>
> 如需以 c + + 撰寫的通用 Windows 平臺應用程式中資源的詳細資訊，請參閱 [定義應用程式資源](/windows/uwp/app-resources/)，或將資源新增至 c + +/cli (受控) 專案，請參閱《 .NET Framework 開發人員指南》中的 [桌面應用程式資源](/dotnet/framework/resources/index) 。

資源可以由各式各樣的元素組成，如下所示：

- 提供資訊給使用者的介面元素，例如點陣圖、圖示或游標。
- 包含資料和應用程式需求的自訂資源。
- 安裝程式 Api 所使用的版本資源。
- 功能表和對話方塊資源。

您可以將新資源加入至您的專案，並使用適當的資源編輯器修改那些資源。 大部分 Visual C++ 精靈會自動為您的專案產生 .rc 檔案。

> [!NOTE]
> **資源編輯器**和**資源檢視**無法在 Express 版本中使用。

若要手動將資源檔新增至受管理的專案，請參閱 [建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 本文包含如何存取資源、顯示靜態資源，以及將資源字串指派給屬性。

若要在受控應用程式中全球化和當地語系化資源，請參閱 [全球化和當地語系化 .NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="in-this-section"></a>本節內容

[資源檔](../windows/resource-files-visual-studio.md)<br/>
描述資源檔，以及它們在 Windows 桌面應用程式中的使用方式。 也提供文章的連結，說明如何使用資源檔。

[ (符號的資源識別碼) ](../windows/symbols-resource-identifiers.md)<br/>
描述符號，並提供如何使用 **資源符號** 對話方塊，來管理專案中符號的相關資訊。

[資源編輯器](../windows/resource-editors.md)<br/>
描述 Visual Studio 中提供的資源編輯器，以及您可以使用每個編輯器修改的資源類型。 也提供使用每個編輯器之詳細資訊的連結。

## <a name="related-sections"></a>相關章節

[Visual Studio 中的 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
提供 Visual C++ 文件的連結。

[與我們交談](/visualstudio/ide/talk-to-us)<br/>
提供如何使用文件集、連絡產品支援，以及採用協助工具功能之資訊的連結。

## <a name="see-also"></a>另請參閱

[Windows 桌面應用程式](./desktop-applications-visual-cpp.md)<br/>
[功能表和其他資源](/windows/win32/menurc/resources)
