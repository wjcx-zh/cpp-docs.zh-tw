---
title: 建立僅含資源的 DLL
description: 如何在 Visual Studio 中建立僅限資源的 DLL。
ms.date: 01/27/2020
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
no-loc:
- noentry
ms.openlocfilehash: ef79de77e35cbef6acd4af1cec82a4edc1b7d105
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821339"
---
# <a name="creating-a-resource-only-dll"></a>建立僅含資源的 DLL

僅限資源的 DLL 是包含任何資源（例如圖示、點陣圖、字串和對話方塊）的 DLL。 使用僅限資源的 DLL 是在多個程式之間共用相同資源集的好方法。 這也是為應用程式提供針對多種語言當地語系化之資源的好方法。 如需詳細資訊，請參閱[MFC 應用程式中的當地語系化資源：附屬 dll](localized-resources-in-mfc-applications-satellite-dlls.md)。

## <a name="create-a-resource-only-dll"></a>建立僅限資源的 DLL

若要建立僅限資源的 DLL，您可以建立新的 Windows DLL （非 MFC）專案，並將您的資源新增至專案：

::: moniker range="vs-2015"

1. 在 [**新增專案**] 對話方塊中，選取 [ **Win32 專案**]。 輸入 [專案] 和 [方案名稱]，然後選擇 **[確定]**。

1. 在 [ **Win32 應用程式]** 中，選取 [**應用程式設定**]。 選擇 [**應用程式類型**] [ **DLL**]。 在 [其他選項] **** 下，選取 [空專案] ****。 選擇 **[完成]** 以建立專案。

1. 建立新的資源腳本，其中包含 DLL （例如字串或功能表）的資源。 儲存 `.rc` 檔案。

1. 在 [**專案**] 功能表上，選取 [**加入現有專案**]，然後`.rc`將新檔案插入專案中。

1. 指定[/NOENTRY](reference/noentry-no-entry-point.md)連結器選項。 `/NOENTRY`防止連結器將的參考`_main`連結到 DLL;建立僅限資源的 DLL 時，需要這個選項。

1. 建置 DLL。

::: moniker-end
::: moniker range=">=vs-2017"

1. 在 [**新增專案**] 對話方塊中選取 [ **Windows 桌面 Wizard]** ，然後選擇 [**下一步**]。 在 [**設定您的新專案**] 頁面上，輸入專案和方案名稱，然後選擇 [**建立**]。

1. 在 [ **Windows 桌面專案**] 對話方塊中，選取 [**動態連結程式庫**] 的**應用程式類型**。 在 [其他選項] **** 下，選取 [空專案] ****。 選擇 **[確定]** 以建立專案。

1. 建立新的資源腳本，其中包含 DLL （例如字串或功能表）的資源。 儲存 `.rc` 檔案。

1. 在 [**專案**] 功能表上，選取 [**加入現有專案**]，然後`.rc`將新檔案插入專案中。

1. 指定[/NOENTRY](reference/noentry-no-entry-point.md)連結器選項。 `/NOENTRY`防止連結器將的參考`_main`連結到 DLL;建立僅限資源的 DLL 時，需要這個選項。

1. 建置 DLL。

::: moniker-end

## <a name="use-a-resource-only-dll"></a>使用僅限資源的 DLL

使用僅限資源 DLL 的應用程式應該呼叫[LoadLibraryEx](loadlibrary-and-afxloadlibrary.md)或相關的函式，以明確連結到 DLL。 若要存取資源，請呼叫泛型函`FindResource`式`LoadResource`和，以在任何類型的資源上運作。 或者，呼叫下列其中一個資源特有的函式：

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

應用程式應該在`FreeLibrary`完成使用資源時呼叫。

## <a name="see-also"></a>請參閱

[使用資源檔](../windows/working-with-resource-files.md)\
[在 Visual Studio 中建立 C++ DLL](dlls-in-visual-cpp.md)
