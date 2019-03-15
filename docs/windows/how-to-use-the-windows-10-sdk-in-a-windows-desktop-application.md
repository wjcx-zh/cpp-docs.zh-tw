---
title: HOW TO：使用 Windows 10 SDK，在 Windows 桌面應用程式
ms.custom: get-started-article
ms.date: 07/12/2018
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
ms.openlocfilehash: 25ef3674a7ab741f20a07d6e65d1b5524fb88d5f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809921"
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>HOW TO：使用 Windows 10 SDK，在 Windows 桌面應用程式

當您在 Visual Studio 2017 中建立傳統 Windows 桌面專案時，它會設定預設為使用已安裝 c + + 桌面工作負載，或上次更新時所安裝的 Windows 10 sdk 版本來建置。 這個版本的 Windows SDK 是相容的 Windows 7 和更新版本。 請參閱[使用 Windows 標頭](/windows/desktop/WinProg/using-the-windows-headers)的目標設為特定的 Windows 版本的詳細資訊。

如果您想要的目標是舊版的 SDK，您可以開啟**專案 |屬性**，然後選擇 從可用的 Windows SDK 版本下拉式清單中的其他 SDK 版本。

從 Visual Studio 2015 和 Windows 10 SDK 開始，CRT 程式庫已分成兩個部分 (ucrtbase) 包含的函式可接受用於通用 Windows 應用程式，以及包含其他項目 (vcruntime140)。 由於 Windows 10 SDK 包含新的函式，例如許多 C99 函式，因此您必須遵循下列步驟以使用這些函式。 請參閱 [CRT Library Features](../c-runtime-library/crt-library-features.md)。

### <a name="to-target-the-windows-10-sdk"></a>以 Windows 10 SDK 為目標

1. 確定已安裝 Windows 10 SDK。 Windows 10 SDK 已安裝的一部分**使用 c + + 的桌面開發**工作負載。 獨立版本[下載和工具適用於 Windows 10](https://developer.microsoft.com/windows/downloads)。

2. 開啟專案節點的捷徑功能表，然後選擇 [重定 SDK 版本目標] 。

   ![重定 SDK 版本目標](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")

   [檢閱方案動作]  對話方塊隨即出現。

   ![檢閱方案動作](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")

3. 在 **目標平台版本**下拉式清單中，選擇您想要為目標的 Windows 10 sdk 版本。 選擇 [確定] 按鈕以套用變更。

   請注意，此處的 8.1 是指 Windows SDK 版本，該版本也與舊版 Windows 8、Windows Server 2012、Windows 7、Windows Server 2008 和 Windows Vista 相容。

   如果這個步驟成功，則會在 [輸出] 視窗中顯示下列文字：

   `Retargeting End: 1 completed, 0 failed, 0 skipped`

4. 開啟專案屬性，在 [組態屬性]、[一般]  區段中，注意 [Windows 目標平台版本] 的值。 變更此處的值，會與遵循這個程序有相同的效果。 請參閱 [General Property Page (Project)](../build/reference/general-property-page-project.md)。

   ![平台版本為目標](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")

   這個動作會變更專案巨集的值，包括標頭檔和程式庫檔案的路徑。 若要查看變更的內容，在**Visual c + + 目錄**一節**專案屬性**對話方塊中，選擇其中一個屬性，例如**Include 目錄**，選擇開啟下拉式清單中，然後選擇 \<編輯 >。 [Include 目錄]  對話方塊隨即出現。

   ![包含目錄對話方塊](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")

   選擇**巨集 >>** 按鈕，然後向下捲動到 Windows SDK 巨集，以查看所有的新值的巨集的清單。

   ![Windows SDK 巨集](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")

5. 如有需要，請針對其他專案重複步驟，並重建方案。

### <a name="to-target-the-windows-81-sdk"></a>以 Windows 8.1 SDK 為目標

1. 開啟專案節點的捷徑功能表，然後選擇 [重定 SDK 版本目標] 。

2. 在 **目標平台版本**下拉式清單中，選擇**8.1**。

## <a name="see-also"></a>另請參閱

[Windows 桌面應用程式 （Visual c + +）](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)