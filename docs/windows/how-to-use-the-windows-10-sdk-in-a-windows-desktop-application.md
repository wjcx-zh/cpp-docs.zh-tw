---
title: 作法：在 Windows 桌面應用程式中使用 Windows 10 SDK
ms.custom: get-started-article
ms.date: 07/12/2018
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: 8dbf18d24c0369507743c3c1da624838f9ab4703
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513830"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>作法：在 Windows 桌面應用程式中使用 Windows 10 SDK

當您在 Visual Studio 2017 中建立傳統 Windows 桌面專案時, 預設會將它設定為使用安裝或上次更新C++桌面工作負載時所安裝的 WINDOWS 10 SDK 版本來建立。 此 Windows SDK 版本與 Windows 7 和更新版本相容。 如需以特定 Windows 版本為目標的詳細資訊, 請參閱[使用 Windows 標頭](/windows/win32/WinProg/using-the-windows-headers)。

如果您想要將目標設為舊版的 SDK, 您可以開啟 [**專案] |[屬性**], 然後從 [Windows SDK 版本] 下拉式清單中提供的其他 SDK 版本進行選擇。

從 Visual Studio 2015 和 Windows 10 SDK 開始, CRT 程式庫分成兩個部分, 一個 (ucrtbase.dll) 包含可在通用 Windows 應用程式中使用的函式, 另一個包含其他專案 (vcruntime140)。 由於 Windows 10 SDK 包含新的函式，例如許多 C99 函式，因此您必須遵循下列步驟以使用這些函式。 請參閱 [CRT Library Features](../c-runtime-library/crt-library-features.md)。

### <a name="to-target-the-windows-10-sdk"></a>以 Windows 10 SDK 為目標

1. 確定已安裝 Windows 10 SDK。 Windows 10 SDK 是以工作負載的**桌面開發C++** 的一部分進行安裝。 [Windows 10 的下載與工具](https://developer.microsoft.com/windows/downloads)提供獨立版本。

2. 開啟專案節點的捷徑功能表，然後選擇 [重定 SDK 版本目標]。

   ![目標 SDK 版本](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")

   [檢閱方案動作] 對話方塊隨即出現。

   ![仲裁者案動作](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

3. 在 [**目標平臺版本**] 下拉式清單中, 選擇您想要設為目標的 WINDOWS 10 SDK 版本。 選擇 [確定] 按鈕以套用變更。

   請注意，此處的 8.1 是指 Windows SDK 版本，該版本也與舊版 Windows 8、Windows Server 2012、Windows 7、Windows Server 2008 和 Windows Vista 相容。

   如果這個步驟成功，則會在 [輸出] 視窗中顯示下列文字：

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

4. 開啟專案屬性，在 [組態屬性]、[一般] 區段中，注意 [Windows 目標平台版本]的值。 變更此處的值，會與遵循這個程序有相同的效果。 請參閱 [General Property Page (Project)](../build/reference/general-property-page-project.md)。

   ![目標平臺版本](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   這個動作會變更專案巨集的值，包括標頭檔和程式庫檔案的路徑。 若要查看變更的內容, 請在 [**專案屬性**] 對話方塊的 [**視覺C++目錄**] 區段中, 選擇其中一個屬性 (例如**Include 目錄**), 選擇開啟下拉式清單\<, 然後選擇 [編輯 >]。 [Include 目錄] 對話方塊隨即出現。

   [![包含目錄] 對話方塊](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   選擇 [**宏 > >** ] 按鈕, 然後將宏清單向下卷到 [Windows SDK 宏], 以查看所有新的值。

   ![Windows SDK 宏](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

5. 如有需要，請針對其他專案重複步驟，並重建方案。

### <a name="to-target-the-windows-81-sdk"></a>以 Windows 8.1 SDK 為目標

1. 開啟專案節點的捷徑功能表，然後選擇 [重定 SDK 版本目標]。

2. 在 [**目標平臺版本**] 下拉式清單中, 選擇 [ **8.1**]。

## <a name="see-also"></a>另請參閱

[Windows 桌面應用程式 ( C++Visual)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)