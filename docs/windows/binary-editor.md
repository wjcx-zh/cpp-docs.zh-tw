---
title: 二進位編輯器 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary.F1
dev_langs:
- C++
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 86dd69a893c589ad4ebba06c2577925eae959f40
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313687"
---
# <a name="binary-editor-c"></a>二進位編輯器 （c + +）

> [!WARNING]
> **二進位編輯器**不適用於 Express 版本。

二進位編輯器允許您在二進位層級，以十六進位或 ASCII 格式編輯任何資源。 您也可以使用 [[尋找命令]](/visualstudio/ide/reference/find-command) 搜尋 ASCII 字串或十六進位位元組。 您應該使用**二進位**編輯器，您需要檢視或次要時，才會變更為自訂資源 」 或 「 不支援的 Visual Studio 環境的資源類型。

若要開啟 **二進位編輯器**，先選擇**檔案** > **新增** > **檔案**從主功能表中，選取您想要編輯，然後按一下下拉箭號旁邊的檔案**開放**按鈕，然後選擇**開啟** > **二進位編輯器**。

> [!CAUTION]
> 在二進位編輯器中編輯諸如對話方塊、影像或功能表等資源，是很危險的事。 不正確的編輯可能會損毀資源，讓它在原生編輯器中無法讀取。

> [!TIP]
> 在使用時**二進位**編輯器，在許多情況下，您可以按一下滑鼠右鍵以顯示資源特定命令的捷徑功能表。 可用的命令取決於游標所指項目。 例如，如果您按一下指向時**二進位**含有所選十六進位值編輯器中，快顯功能表會顯示**剪下**，**複製**，和**貼上**命令。

具有**二進位**編輯器，您可以：

- [開啟資源進行二進位編輯](../windows/opening-a-resource-for-binary-editing.md)

- [編輯二進位資料](../windows/editing-binary-data.md)

- [尋找二進位資料](../windows/finding-binary-data.md)

- [建立新的自訂或資料資源](../windows/creating-a-new-custom-or-data-resource.md)

## <a name="managed-resources"></a>Managed 資源

您可以使用[影像編輯器](../windows/image-editor-for-icons.md)並**二進位**編輯器來處理中的資源檔 managed 專案。 您想要編輯的任何 Managed 資源皆必須為連結的資源。 Visual Studio 資源編輯器並不支援對內嵌資源的編輯功能。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

無

## <a name="see-also"></a>另請參閱

[資源編輯器](../windows/resource-editors.md)