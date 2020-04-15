---
title: 靜態程式庫 (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 3c4bfd28b805903a2e596ef6d648ff31b0b8261c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358102"
---
# <a name="static-libraries-ccx"></a>靜態程式庫 (C++/CX)

通用 Windows 平臺 (UWP) 應用中使用的靜態庫可以包含 ISO 標準 C++代碼 (包括 STL 類型),還可以調用未從 Windows 運行時應用平臺排除的 Win32 API。 靜態庫使用 Windows 運行時元件,並可能創建具有某些限制的 Windows 執行時元件。

## <a name="creating-static-libraries"></a>建立靜態程式庫

創建新項目的說明因已安裝的 Visual Studio 版本而異。 要查看您首選版本的 Visual Studio 的文件,請使用**版本**選擇器控制項。 它位於此頁面的目錄頂部。

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>在 Visual Studio 2019 建立 UWP 靜態庫

1. 在功能表列上，選擇 [檔案]** [新增]** > ** [專案]** > ****，以開啟 [建立新專案]**** 對話方塊。

1. 在對話框的頂部,將**語言**設定為**C++,** 將**平台**設定為**Windows,** 並將**項目類型**設定為**UWP**。

1. 從篩選的項目類型清單中,選擇**靜態庫(通用 Windows - C++/CX),** 然後選擇 **「下一步**」 。。 在下一頁中,為專案指定名稱,並根據需要指定專案位置。

1. 選擇 [建立] **** 按鈕以建立專案。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>在 Visual Studio 2017 或 Visual Studio 2015 中建立 UWP 靜態庫

1. 在選單列上,選擇 **「檔** > **新專案** > **」。。** 在**視覺C++** > **Windows 通用**選擇**靜態庫(通用視窗)。**

1. 在**解決方案資源管理員**中,開啟專案的快捷方式選單,然後選擇**屬性**。 在「**屬性」** 對話框中,在 **「設定屬性** > **C/C++」** 頁上,將 **「使用 Windows 執行時擴展**時間設定為 **」(/ZW)。**

::: moniker-end

編譯新的靜態庫時,如果調用為 UWP 應用排除的 Win32 API,編譯器將引發錯誤 C3861,"找不到標識符"。 要尋找 Windows 執行時支援的替代方法,請參閱[UWP 應用中 Windows API 的替代方法](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)。

如果將靜態庫專案C++添加到UWP應用解決方案,則可能需要更新庫專案的屬性設置,以便UWP支援屬性設置為 **"是**"。 如果沒有此設置,代碼將生成和連結,但在嘗試驗證 Microsoft 應用商店的應用時將發生錯誤。 靜態程式庫必須以使用它的專案相同的編譯器設定進行編譯。

如果您使用會建立公用 `ref` 類別、公用介面類別或公用實值類別的靜態程式庫，連結器將會引發下列警告：

> **警告 LNK4264:** 將使用 /ZW 編譯的物件檔存檔到靜態庫中;請注意,在創作 Windows 運行時類型時,不建議與包含 Windows 運行時元數據的靜態庫連結。

僅當靜態庫未生成在庫本身之外使用的 Windows 運行時元件時,才能安全地忽略該警告。 如果程式庫不會使用它所定義的元件，則連結器最佳化會將實作去除，即使公用中繼資料包含型別資訊。 這表示靜態程式庫中的公用元件會進行編譯，但不會在執行階段啟動。 因此,任何 Windows 運行時元件(供其他元件或應用使用)都必須在動態連結庫(DLL) 中實現。

## <a name="see-also"></a>另請參閱

[執行緒和封送處理](../cppcx/threading-and-marshaling-c-cx.md)
