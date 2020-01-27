---
title: 如何：在 Windows 桌面應用程式中使用 Windows 10 SDK
description: 如何將 Windows 桌面應用程式專案中的目標 SDK 版本設定為使用 Windows 10 SDK。
ms.custom: get-started-article
ms.date: 01/22/2020
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: c1d71b591398453f7cee02aa22cd2e377991588f
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725730"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>如何：在 Windows 桌面應用程式中使用 Windows 10 SDK

當您在 Visual Studio 中建立新的傳統 Windows 桌面專案時，預設會以 Windows 10 SDK 為目標。 當您安裝C++桌面工作負載時，Visual Studio 會安裝此 SDK 的版本。 Windows 10 SDK 支援撰寫 Windows 7 SP1 和更新版本的程式碼。 如需以特定版本的 Windows 為目標的詳細資訊，請參閱[使用 Windows 標頭](/windows/win32/WinProg/using-the-windows-headers)和[更新 WINVER 和 _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md)。

當您升級現有的專案時，可以選擇：您可以繼續使用專案中指定的目標 Windows SDK。 或者，您可以將專案的目標重定為使用 Windows 10 SDK。 有了 Windows 10 SDK，您就能獲得最新作業系統和語言標準的支援優勢。

## <a name="use-the-right-windows-sdk-for-your-project"></a>使用適用于您專案的 Windows SDK

從 Visual Studio 2015 開始，C 執行時間（CRT）程式庫分成兩個部分：一個部分 ucrtbase.dll，其中包含您可以在通用 Windows 應用程式中使用的標準 C 和 Microsoft 特有 CRT 函式。 此程式庫現在稱為通用 CRT 或 UCRT，並已移至 Windows 10 SDK。 UCRT 包含許多新功能，例如支援最新C++語言標準所需的 C99 函數。 原始 CRT 的另一個部分是 vcruntime。 其中包含 C 執行時間支援、啟動和終止程式碼，以及其他未進入 UCRT 的專案。 Vcruntime 程式庫會隨著C++編譯器和工具組安裝在 Visual Studio 中。 如需詳細資訊，請參閱[CRT 程式庫功能](../c-runtime-library/crt-library-features.md)。

UCRT 現在是安裝在 Windows 10 每個版本上的系統元件。 它也可作為所有舊版受支援 Windows 版本的可安裝元件。 您可以使用 Windows 10 SDK，以所有支援的 Windows 版本為目標。 如需所支援作業系統的完整清單，請參閱[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)。

若要在 Visual Studio 2015 之前從專案版本升級時，將專案的目標重定為使用 Windows 10 SDK，請遵循下列步驟：

### <a name="to-target-the-windows-10-sdk"></a>以 Windows 10 SDK 為目標

1. 確定已安裝 Windows 10 SDK。 Windows 10 SDK 是以工作負載的**桌面開發C++** 的一部分進行安裝。 [Windows 10 的下載與工具](https://developer.microsoft.com/windows/downloads)提供獨立版本。

1. 開啟專案節點的快捷方式功能表，然後選擇 [重定**專案的目標**]。 （在舊版的 Visual Studio 中，選擇 [重定**SDK 版本的目標**）]。[**仲裁者案動作**] 對話方塊隨即出現。

   ![仲裁者案動作](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

1. 在 [**目標平臺版本**] 下拉式清單中，選擇您想要設為目標的 WINDOWS 10 SDK 版本。 一般來說，我們建議您選擇最新安裝的版本。 選擇 [**確定]** 按鈕以套用變更。

   此內容中的8.1 是指 Windows 8.1 SDK。

   如果這個步驟成功，則會在 [輸出] 視窗中顯示下列文字：

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

1. 開啟 [專案屬性] 對話方塊。 在 [設定**屬性**] >  **[一般**] 區段中，注意 [ **Windows 目標平臺版本**] 的值。 變更此處的值，會與遵循這個程序有相同的效果。 如需詳細資訊，請參閱[一般屬性頁 (專案)](../build/reference/general-property-page-project.md)。

   ![目標平臺版本](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   這個動作會變更專案巨集的值，包括標頭檔和程式庫檔案的路徑。 若要查看變更的內容，請開啟 [**專案屬性**] 對話方塊的 [**視覺C++目錄**] 區段。 選取其中一個屬性，例如 [ **Include 目錄**]。 然後，開啟屬性值的下拉式清單，然後選擇 [ **\<編輯 >** ]。 [Include 目錄] 對話方塊隨即出現。

   ![[包含目錄] 對話方塊](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   選擇 [**宏 > >** ] 按鈕，然後將宏清單向下卷到 [Windows SDK 宏]，以查看所有新的值。

   ![Windows SDK 宏](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

1. 視需要為其他方案專案重複重定程式，並重建方案。

### <a name="to-target-the-windows-81-sdk"></a>以 Windows 8.1 SDK 為目標

1. 在方案總管中開啟專案節點的快捷方式功能表，然後選擇 [重定**目標專案**]。 （在舊版的 Visual Studio 中，選擇 [重定**SDK 版本的目標**）]。

2. 在 [**目標平臺版本**] 下拉式清單中，選擇 [ **8.1**]。

## <a name="see-also"></a>請參閱

[逐步解說：建立傳統 Windows 桌面應用程式C++（）](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)
