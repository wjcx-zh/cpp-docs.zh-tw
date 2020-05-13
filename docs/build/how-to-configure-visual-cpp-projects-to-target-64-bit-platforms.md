---
title: 如何：將 Visual Studio c + + 專案設定為以64位、x64 平臺為目標
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: 762fd5d6ddbb55713cf2fc5e34cb33fb91b08eb9
ms.sourcegitcommit: ce3393846c86e7905ff0c86e4cd6610476809585
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68492247"
---
# <a name="how-to-configure-visual-studio-c-projects-to-target-64-bit-x64-platforms"></a>如何：將 Visual Studio c + + 專案設定為以64位、x64 平臺為目標

您可以使用 Visual Studio IDE 中的專案設定，將 c + + 應用程式設定為以64位 x64 平臺為目標。 您也可以將 Win32 專案設定移轉至 64 位元專案組態。

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>設定 C++ 應用程式鎖定 64 位元平台

1. 請開啟您想要設定的 C++ 專案。

1. 開啟該專案的屬性頁面。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](working-with-project-properties.md)。

   > [!NOTE]
   > 若為 .net 專案，請確定已在 [ ** \<專案名稱]> [屬性頁**] 對話方塊中選取 [設定**屬性**] 節點或其子節點之一;否則，[ **Configuration Manager** ] 按鈕仍然無法使用。

1. 選擇 [組態管理員] **** 按鈕開啟 [組態管理員] **** 對話方塊。

1. 在 [使用中的**方案平臺**] 下拉式清單中，選取 [ ** \<新增 ...] >** 選項，以開啟 [**新增方案平臺**] 對話方塊。

1. 在 [**類型] 或 [選取**新平臺] 下拉式清單中，選取64位目標平臺。

   > [!NOTE]
   > 在 [新增方案平台] **** 對話方塊中，您可以使用 [複製設定值來源] **** 選項將現有的專案設定複製到新的 64 位元專案組態。

1. 選擇 [確定] **** 按鈕。 上個步驟所選取的平台會出現在 [組態管理員] **** 對話方塊的 [使用中的方案平台] **** 之下。

1. 選擇 [ **Configuration Manager** ] 對話方塊中的 [**關閉**] 按鈕，然後在 [ ** \<專案名稱> 屬性頁**] 對話方塊中選擇 [**確定]** 按鈕。

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>將 Win32 專案設定複製到 64 位元專案組態

- 當 [新增方案平台] **** 對話方塊在您設定專案鎖定 64 位元平台時開啟，請在 [複製設定值來源] **** 下拉式清單中選取 [Win32] ****。 這些專案設定會自動在專案層級上更新：

  - [/MACHINE](reference/machine-specify-target-platform.md) 連結器選項會設為 **/MACHINE:X64**。

  - [登錄輸出]**** 已關閉。 如需詳細資訊，請參閱 [Linker Property Pages](reference/linker-property-pages.md)。

  - [目標環境]**** 設為 **/env x64**。 如需詳細資訊，請參閱[MIDL 屬性頁](reference/midl-property-pages.md)。

  - [驗證參數]**** 已清除並重設為預設值。 如需詳細資訊，請參閱[MIDL 屬性頁](reference/midl-property-pages.md)。

  - 如果 [偵錯資訊格式] **** 在 Win32 專案組態中設為 **/ZI** ，則在 64 位元專案組態中就會設為 **/Zi** 。 如需詳細資訊，請參閱 [/Z7、/Zi、/ZI (偵錯資訊格式)](reference/z7-zi-zi-debug-information-format.md)。

  > [!NOTE]
  > 如果它們在檔案層級上覆寫，這些專案屬性全都不會變更。

## <a name="see-also"></a>請參閱

[設定適用於 64 位元、x64 目標的 C++ 專案](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Debug 64 位應用程式](/visualstudio/debugger/debug-64-bit-applications)
