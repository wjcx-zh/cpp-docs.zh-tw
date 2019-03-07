---
title: 使用資源檔 （c + +）
ms.date: 02/14/2019
helpviewer_keywords:
- resources [C++], about resources
- resources [C++], about resource files
- resource files [C++], about resource files
ms.assetid: 2699a539-b369-4b78-80f0-df03eb7b6780
ms.openlocfilehash: 8edc860db453c4ee9e0dd3fdacb18bbde662accb
ms.sourcegitcommit: b4645761ce5acf8c2fc7a662334dd5a471ea976d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/07/2019
ms.locfileid: "57562961"
---
# <a name="working-with-resource-files"></a>使用資源檔

> [!WARNING]
> 本節適用於以 C++ 撰寫的 Windows 桌面應用程式。
>
> 在 c + + 撰寫的通用 Windows 平台應用程式中資源的詳細資訊，請參閱[定義應用程式資源](/windows/uwp/app-resources/)，或將資源新增至 C + + /cli （管理） 的 CLI 專案，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中.NET Framework 開發人員指南。

資源可以組成各種不同的項目，例如：

- 提供資訊給使用者，例如點陣圖、 圖示或游標的介面項目。
- 包含資料和應用程式的自訂資源需求。
- 安裝程式 Api 所使用的版本資源。
- 功能表和對話方塊資源。

您可以將新資源加入至您的專案，並使用適當的資源編輯器修改那些資源。 大部分 Visual C++ 精靈會自動為您的專案產生 .rc 檔案。

> [!NOTE]
> **資源編輯器**並**資源檢視**無法在 Express 版中使用。

若要手動加入資源檔加入 managed 專案，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 這篇文章包含如何存取資源、 顯示靜態資源及指派資源字串給屬性。

若要進行全球化和當地語系化受管理的應用程式中的資源，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="in-this-section"></a>本節內容

[資源檔](../windows/resource-files-visual-studio.md)<br/>
描述資源檔，以及它們在 Windows 桌面應用程式中的使用方式。 也提供文章會說明如何使用資源檔的連結。

[資源識別項 (符號)](../windows/symbols-resource-identifiers.md)<br/>
描述符號，並提供如何使用 **資源符號** 對話方塊，來管理專案中符號的相關資訊。

[資源編輯器](../windows/resource-editors.md)<br/>
描述在 Visual Studio 和您可以修改每個編輯器的資源類型提供的資源編輯器。 也提供使用每個編輯器的詳細資訊連結。

## <a name="related-sections"></a>相關章節

[Visual C++](../visual-cpp-in-visual-studio.md)<br/>
提供 Visual C++ 文件的連結。

[告訴我們](/visualstudio/ide/talk-to-us)<br/>
提供如何使用文件集、連絡產品支援，以及採用協助工具功能之資訊的連結。

## <a name="see-also"></a>另請參閱

[Windows 桌面應用程式](../windows/windows-desktop-applications-cpp.md)<br/>
[功能表與其他資源](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)