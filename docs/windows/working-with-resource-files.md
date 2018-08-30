---
title: Working with Resource Files |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], about resources
- resources [C++], about resource files
- resource files, about resource files
ms.assetid: 2699a539-b369-4b78-80f0-df03eb7b6780
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d96b9430cd5a6a4a9f3d65ab60c49a38b0530db7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211093"
---
# <a name="working-with-resource-files"></a>使用資源檔

> [!WARNING]
> 本節適用於以 C++ 撰寫的 Windows 桌面應用程式。 在 c + + 撰寫的通用 Windows 平台應用程式中資源的詳細資訊，請參閱[定義應用程式資源](https://msdn.microsoft.com/476ea844-632c-4467-9ce3-966be1350dd4)。
>
> 如需將資源新增至 C + + /cli 專案，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。

資源可以由大範圍的項目組成，包括向使用者提供資訊的介面項目 (例如點陣圖、圖示或游標)；包含應用程式所需資料的自訂資源；由設定 API 使用的版本資源；以及功能表和對話方塊資源。

您可以將新資源加入至您的專案，並使用適當的資源編輯器修改那些資源。 大部分 Visual C++ 精靈會自動為您的專案產生 .rc 檔案。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="in-this-section"></a>本節內容

[資源檔](../windows/resource-files-visual-studio.md)  
描述資源檔及其在 Windows 桌面應用程式中的使用方式。 同時會提供描述如何使用資源檔之主題的連結。

[符號：資源識別項](../windows/symbols-resource-identifiers.md)  
描述符號，並提供如何使用 **資源符號** 對話方塊，來管理專案中符號的相關資訊。

[資源編輯器](../windows/resource-editors.md)  
描述 Visual Studio 中提供的資源編輯器，您可以使用每一個編輯器修改的資源類型，並提供如何使用每一個編輯器之詳細資訊的連結。

## <a name="related-sections"></a>相關章節

[Visual C++](../visual-cpp-in-visual-studio.md)  
提供 Visual C++ 文件的連結。

[Visual Studio 簡介](https://msdn.microsoft.com/99997089-56ff-4d60-81a9-447062dc98ac)  
描述使用相同整合式開發環境 (IDE) 之所有開發工具的完整集合，容許它們在建立混合語言方案時共用工具和設施。

[告訴我們](/visualstudio/ide/talk-to-us)  
提供如何使用文件集、連絡產品支援，以及採用協助工具功能之資訊的連結。

## <a name="see-also"></a>另請參閱

[Windows 桌面應用程式](../windows/windows-desktop-applications-cpp.md)  
[功能表和其他資源](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)