---
title: 疑難排解組建自訂
ms.date: 11/04/2016
helpviewer_keywords:
- build events [C++], troubleshooting
- builds [C++], build events
- troubleshooting [C++], builds
- build steps [C++], troubleshooting
- events [C++], build
- builds [C++], troubleshooting
- custom build steps [C++], troubleshooting
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
ms.openlocfilehash: 7a45b449dc9c3c4c81add37bbac0813c81133203
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315244"
---
# <a name="troubleshooting-build-customizations"></a>疑難排解組建自訂

如果您的自訂建置步驟或事件行為不如預期，有幾件事您可以嘗試，以了解發生什麼錯誤。

- 請確定您的自訂建置步驟所產生的檔案，符合您宣告為輸出的檔案。

- 如果您的自訂建置步驟產生的任何檔案是其他建置步驟 (自訂或其他) 的輸入或相依性，請確定那些檔案已新增至您的專案。 並且確定使用那些檔案的工具會在自訂建置步驟之後執行。

- 若要顯示自訂建置步驟實際進行什麼，請新增 `@echo on` 作為第一個命令。 建置事件與建置步驟會放在暫時的 .bat 檔，並在建置專案時執行。 因此，您可以新增錯誤檢查到您的建置事件或建置步驟命令。

- 檢查中繼檔案目錄中的組建記錄檔，以查看實際執行的情況。 組建記錄檔的名稱與路徑由 **MSBuild** 巨集運算式 **$(IntDir)\\$(MSBuildProjectName).log** 代表。

- 修改您的專案設定可收集超過組建記錄檔中的預設資訊量。 在 [ **工具** ] 功能表上按一下 [ **選項**]。 在 [選項] 對話方塊方塊中，按一下 [專案和方案] 節點，然後按一下 [建置並執行] 節點。 然後，在 [MSBuild 專案組建記錄檔詳細資訊] 方塊中，按一下 [詳細]。

- 確認您正在使用的任何檔案名稱或目錄巨集的值。 您可以個別回應巨集，或是將 `copy %0 command.bat` 新增至自訂建置步驟的開頭，這樣會將自訂建置步驟的命令複製到 command.bat，並展開所有巨集。

- 個別地執行自訂建置步驟和建置事件，以檢查其行為。

## <a name="see-also"></a>另請參閱

[了解自訂建置步驟和建置事件](understanding-custom-build-steps-and-build-events.md)
