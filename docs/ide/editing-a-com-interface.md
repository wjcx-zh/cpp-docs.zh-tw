---
title: 編輯 COM 介面 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.com.editing.interfaces
dev_langs:
- C++
helpviewer_keywords:
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 451e7fc6e2a7b4a72188da6b69888bf04b605842
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412355"
---
# <a name="editing-a-com-interface"></a>編輯 COM 介面

您可以使用 [類別檢視] 捷徑功能表中的命令，為 Visual C++ 專案中的 COM 介面定義新的方法和屬性。 此外，您可以從 [工具箱] 為 ActiveX 控制項定義事件。

針對 ATL 和 MFC 型 COM 物件類別，您可以在編輯介面同時編輯類別實作。

> [!NOTE]
>  針對您在 [新增類別] 對話方塊外部定義的介面，Visual C++ 會將方法或屬性新增至 .idl 檔案，並將虛設常式新增至實作方法的類別，即使手動新增這些介面也一樣。

下列三個精靈可協助您自訂現有的介面。 您可以從 [類別檢視] 存取這些介面：

|精靈|專案類型|
|------------|------------------|
|[新增屬性精靈](../ide/names-add-property-wizard.md)|支援 ATL 的 ATL 或 MFC 專案。 以滑鼠右鍵按一下您要新增屬性的介面。<br /><br /> Visual C++ 會偵測專案類型，並據以修改 [新增屬性精靈] 中的選項：<br /><br /> -   針對使用 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)建立之專案中的分配介面 (Dispinterface)，叫用 [新增屬性精靈] 會提供 MFC 特定的選項。<br />-   針對 MFC ActiveX 控制項介面，[新增屬性精靈] 會提供內建方法和屬性清單，您可以直接使用或為您的控制項自訂。<br />-   針對所有其他介面，[新增屬性精靈] 會提供大部分情況下都有用的選項。|
|[新增方法精靈](../ide/add-method-wizard.md)|支援 ATL 的 ATL 或 MFC 專案。 以滑鼠右鍵按一下您要新增方法的介面。<br /><br /> Visual C++ 會偵測專案類型，並據以修改 [新增方法精靈] 中的選項：<br /><br /> -   針對使用 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)建立之專案中的分配介面 (Dispinterface)，叫用 [新增方法精靈] 會提供 MFC 特定的選項。<br />-   針對 MFC ActiveX 控制項介面，[新增方法精靈] 會提供內建方法和屬性清單，您可以直接使用或為您的控制項自訂。<br />-   針對所有其他介面，[新增方法精靈] 會提供大部分情況下都有用的選項。|

此外，您可以在 [類別檢視] 中以滑鼠右鍵按一下物件的控制項類別，然後按一下[實作介面](../ide/implement-interface-wizard.md)，在您的 COM 控制項上實作新的介面。

## <a name="see-also"></a>請參閱

[使用資源檔](../windows/working-with-resource-files.md)<br>
[使用程式碼精靈新增功能](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Visual C++ 專案類型](../ide/visual-cpp-project-types.md)