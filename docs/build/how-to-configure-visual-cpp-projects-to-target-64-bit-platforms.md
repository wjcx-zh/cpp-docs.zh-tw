---
title: HOW TO：設定 Visual c + + 專案，以 64 位元、 x64 平台
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: 21c812efd101c64e250a545d2a40df6adc31c414
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813951"
---
# <a name="how-to-configure-visual-c-projects-to-target-64-bit-x64-platforms"></a>HOW TO：設定 Visual c + + 專案，以 64 位元、 x64 平台

您可以使用 Visual Studio IDE 中的專案組態設定 c + + 應用程式鎖定 64 位元、 x64 平台。 您也可以將 Win32 專案設定移轉至 64 位元專案組態。

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>設定 C++ 應用程式鎖定 64 位元平台

1. 請開啟您想要設定的 C++ 專案。

1. 開啟該專案的屬性頁面。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](working-with-project-properties.md)。

   > [!NOTE]
   > .NET 專案中，請確定 **組態屬性** 中選取節點，或它的子節點，其中 **\<專案名稱 > 屬性頁**  對話方塊中，否則**Configuration Manager**按鈕將仍然無法使用。

1. 選擇 [組態管理員]  按鈕開啟 [組態管理員]  對話方塊。

1. 在 [**作用中的方案平台** 下拉式清單中，選取 **\<新增...>** 選項來開啟 **新增方案平台**] 對話方塊。

1. 在 **輸入或選取新的平台**下拉式清單中選取 64 位元目標平台。

   > [!NOTE]
   > 在 [新增方案平台]  對話方塊中，您可以使用 [複製設定值來源]  選項將現有的專案設定複製到新的 64 位元專案組態。

1. 選擇 [ **確定** ] 按鈕。 上個步驟所選取的平台會出現在 [組態管理員]  對話方塊的 [使用中的方案平台]  之下。

1. 選擇 **關閉** 按鈕 **Configuration Manager** 對話方塊的 ，然後選擇**確定** 按鈕 **\<專案名稱 >屬性頁**  對話方塊。

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>將 Win32 專案設定複製到 64 位元專案組態

- 當 [新增方案平台]  對話方塊在您設定專案鎖定 64 位元平台時開啟，請在 [複製設定值來源]  下拉式清單中選取 [Win32] 。 這些專案設定會自動在專案層級上更新：

  - [/MACHINE](reference/machine-specify-target-platform.md) 連結器選項會設為 **/MACHINE:X64**。

  - [登錄輸出] 已關閉。 如需詳細資訊，請參閱 [Linker Property Pages](reference/linker-property-pages.md)。

  - [目標環境] 設為 **/env x64**。 如需詳細資訊，請參閱[MIDL 屬性頁：一般](reference/midl-property-pages-general.md)。

  - [驗證參數] 已清除並重設為預設值。 如需詳細資訊，請參閱[MIDL 屬性頁：進階](reference/midl-property-pages-advanced.md)。

  - 如果 [偵錯資訊格式]  在 Win32 專案組態中設為 **/ZI** ，則在 64 位元專案組態中就會設為 **/Zi** 。 如需詳細資訊，請參閱 [/Z7、/Zi、/ZI (偵錯資訊格式)](reference/z7-zi-zi-debug-information-format.md)。

  > [!NOTE]
  > 如果它們在檔案層級上覆寫，這些專案屬性全都不會變更。

## <a name="see-also"></a>另請參閱

[設定適用於 64 位元、 x64 的 c + + 專案的目標](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[偵錯 64 位元應用程式](/visualstudio/debugger/debug-64-bit-applications)
