---
title: 靜態程式庫 (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: f62ef03cfdf2f424fd4a50c2e866d73b5bdce7fc
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302936"
---
# <a name="static-libraries-ccx"></a>靜態程式庫 (C++/CX)

在通用 Windows 平臺（UWP）應用程式中使用的靜態程式庫可包含 ISO 標準C++程式碼，包括 STL 類型，以及未從 Windows 執行階段應用程式平臺排除的 Win32 api 呼叫。 靜態程式庫會使用 Windows 執行階段元件，而且可能會建立具有特定限制的 Windows 執行階段元件。

## <a name="creating-static-libraries"></a>建立靜態程式庫


建立新專案的指示會根據您已安裝的 Visual Studio 版本而有所不同。 請確定您在左上角將版本選取器設定為正確的版本。

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>在 Visual Studio 2019 中建立 UWP 靜態程式庫

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]，以開啟 [建立新專案] 對話方塊。

1. 在對話方塊頂端，將 [**語言**] 設定為**C++** ，將 [**平臺**] 設定為 [ **Windows**]，並將 [**專案類型**] 設定為 [ **UWP**]。 

1. 從篩選過的專案類型清單中，選擇 [**靜態程式庫（通用C++Windows-/cx）** ]，然後選擇 **[下一步]** 。 在下一個頁面中，提供專案的名稱，並視需要指定專案位置。

1. 選擇 [建立] 按鈕以建立專案。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>在 Visual Studio 2017 或 Visual Studio 2015 中建立 UWP 靜態程式庫

1. 在功能表列上，選擇 [檔案] > [新增] > [專案]。 在 **[ C++ Visual** > **Windows 通用**] 底下選擇 [**靜態程式庫（通用 Windows）** ]。

1. 在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **屬性**]。 在 [**內容] 對話方塊的 [** 設定**屬性**] > [ **CC++ /** ] 頁面上，將 [**使用 Windows 執行階段延伸**模組] 設為 **[是] （/ZW）** 。

::: moniker-end

當您編譯新的靜態程式庫時，如果您呼叫已針對 UWP 應用程式排除的 WIN32 API，編譯器將會引發錯誤 C3861 「找不到識別碼」。 若要尋找 Windows 執行階段支援的替代方法，請參閱[UWP 應用程式中的 Windows Api 替代方案](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)。

如果您將C++靜態程式庫專案新增至 UWP 應用程式方案，您可能必須更新程式庫專案的屬性設定，讓 UWP support 屬性設定為 **[是]** 。 如果沒有此設定，則程式碼會建立和連結，但當您嘗試驗證 Microsoft Store 的應用程式時，就會發生錯誤。 靜態程式庫必須以使用它的專案相同的編譯器設定進行編譯。

如果您使用會建立公用 `ref` 類別、公用介面類別或公用實值類別的靜態程式庫，連結器將會引發下列警告：

> **警告 LNK4264：** 將以/ZW 編譯的物件檔案封存至靜態程式庫;請注意，撰寫 Windows 執行階段類型時，不建議與包含 Windows 執行階段中繼資料的靜態程式庫連結。

只有當靜態程式庫不會產生在程式庫本身以外使用的 Windows 執行階段元件時，您才可以放心地忽略警告。 如果程式庫不會使用它所定義的元件，則連結器最佳化會將實作去除，即使公用中繼資料包含型別資訊。 這表示靜態程式庫中的公用元件會進行編譯，但不會在執行階段啟動。 基於這個理由，任何要供其他元件或應用程式取用的 Windows 執行階段元件，都必須在動態連結程式庫（DLL）中執行。

## <a name="see-also"></a>請參閱

[執行緒和封送處理](../cppcx/threading-and-marshaling-c-cx.md)
