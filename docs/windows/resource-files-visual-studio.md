---
title: 資源檔 (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resources [C++]
- .rc files [C++]
- resource files [C++]
- resource script files [C++]
- resource script files [C++], Win-32 based applications
- resource script files [C++], files updated when editing resources
- resources [C++], types of resource files
- rct files [C++]
- rc files [C++]
- resource files [C++], types of
- .rct files [C++]
- resource script files [C++], unsupported types
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6db3af430b0274f116eba4445158ddcf55ad1636
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315661"
---
# <a name="resource-files-c"></a>資源檔 (C++)

> [!NOTE]
> 這份資料適用於 Windows 桌面應用程式。 通用 Windows 平台應用程式中資源的詳細資訊，請參閱[定義應用程式資源](/windows/uwp/app-resources/)。
>
> 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。
>
> 。因為 .NET 程式設計語言中的專案不使用資源指令碼檔案，所以您必須從 **方案總管**。 您可以使用 [影像編輯器](../windows/image-editor-for-icons.md) 和 [二進位編輯器](binary-editor.md) 處理 Managed 專案中的資源檔。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。

「資源檔案」一詞表示多種檔案類型，包括：

- 程式的資源指令碼 (.rc) 檔。

- 資源範本 (.rct) 檔。

- 以獨立檔案形態存在的個別資源，例如 .rc 檔案提及的點陣圖、圖示或游標檔。

- 開發環境產生的標頭檔，例如 .rc 檔案提及的 Resource.h。

資源也可以在 [其他檔案類型](../windows/editable-file-types-for-resources.md) 中找到，例如 .exe、.dll 和 .res 檔。 您可以使用專案內的以及不屬於目前專案的資源和資源檔。 您也可以使用不在 Visual studio 開發環境中建立的資源檔。 例如，您可以：

- 使用巢狀和條件限定的資源檔案。

- 更新現有的資源，或將它們轉換成 Visual C++ 格式。

- 從目前的資源檔匯入或匯出圖形資源。

- 包含開發環境無法修改的共用或唯讀識別項 (符號)。

- 在可執行檔 (.exe) 檔案中，包含於目前專案期間不需要編輯 (或您不想要編輯) 的資源，例如數個專案間共用的資源。

- 包含開發環境不支援的類型。

本節涵蓋：

- [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)

- [建立新專案](../windows/how-to-create-a-resource.md)

- [檢視資源指令碼檔案的資源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)

- [以文字格式開啟資源指令碼檔](../windows/how-to-open-a-resource-script-file-in-text-format.md)

- [在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)

- [複製資源](../windows/how-to-copy-resources.md)

- [使用資源範本 (.rct)](../windows/how-to-use-resource-templates.md)

- [匯入及匯出資源](../windows/how-to-import-and-export-resources.md)

- [可編輯的資源檔類型](../windows/editable-file-types-for-resources.md)

- [受資源編輯影響的檔案](../windows/files-affected-by-resource-editing.md)

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)  
[使用資源檔](../windows/working-with-resource-files.md)  
[功能表和其他資源](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)