---
title: 定義助憶鍵 (便捷鍵)
ms.date: 11/04/2016
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls [C++], mnemonics
- access keys [C++], checking
- mnemonics [C++], checking for duplicate
- mnemonics
- mnemonics [C++], dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
ms.openlocfilehash: 8682ab38abebe1c453ef562e8eaac0e627f5c4bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488916"
---
# <a name="defining-mnemonics-access-keys"></a>定義助憶鍵 (便捷鍵)

一般來說，鍵盤使用者輸入的焦點從一個控制項移到另一個對話方塊中 **索引標籤**並**箭號**索引鍵。 不過，您可以定義便捷鍵 （助憶鍵，或按一下 以易記名稱），可讓使用者藉由按下單一索引鍵選擇的控制項。

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>若要定義具有可見標題 （按鈕、 核取方塊和選項按鈕） 的控制項的便捷鍵

1. 選取對話方塊上的控制項。

2. 在 [[屬性] 視窗](/visualstudio/ide/reference/properties-window)，請在**標題**屬性，輸入控制項中，輸入 & 符號的新名稱 (`&`) 您想要為該控制項的便捷鍵的字母前面。 例如，`&Radio1`。

3. 按 **Enter** 鍵。

   在顯示的標題中表示的存取金鑰，比方說，就會出現底線**R**adio1。

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>若要定義沒有可見標題控制項的便捷鍵

1. 使用時，進行控制項的標題**靜態文字**控制中[工具箱](/visualstudio/ide/reference/toolbox)。

2. 在靜態文字的標題中，輸入連字號 (`&`) 您想要作為便捷鍵的字母前面。

3. 請確定靜態文字控制項前面的控制項之前的定位順序。

對話方塊中的所有便捷鍵應該都是唯一的。

### <a name="to-check-for-duplicate-access-keys"></a>若要檢查有重複的便捷鍵

1. 在 **格式**功能表上，按一下**檢查助憶鍵**。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[控制項](../mfc/controls-mfc.md)