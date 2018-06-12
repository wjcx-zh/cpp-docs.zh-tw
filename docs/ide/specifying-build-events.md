---
title: 指定建置事件 | Microsoft Docs
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
dev_langs:
- C++
helpviewer_keywords:
- Pre-Link event
- build events [C++], specifying
- custom build steps [C++], build events
- builds [C++], events
- events [C++], build
- builds [C++], customizing C++
- build events [C++]
- post-build events
ms.assetid: 788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5940f0d6efaec402a4a85ed659f42d7eab1bf91d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33334960"
---
# <a name="specifying-build-events"></a>指定建置事件

您可以使用建置事件指定要在建置開始之前、連結程序之前，或建置完成之後執行的命令。

只有在建置成功到達建置流程中的這些點時，建置事件才會執行。 如果建置中發生錯誤，「建置後」事件不會發生；如果在連結階段之前發生錯誤，「連結前」或「建置後」事件都不會發生。 此外，如果不需要連結檔案，「連結前」事件不會發生。 未包含連結步驟的專案也不會提供「連結前」事件。

如果不需要建置檔案，則不會發生任何建置事件。

如需建置事件的一般資訊，請參閱[了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)。

### <a name="to-specify-a-build-event"></a>若要指定建置事件

1. 在 [方案總管] 中，選取您想要指定建置事件的專案。

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。

1. 在 [建置事件] 資料夾中，選取建置事件屬性頁。

1. 指定與建置事件建立關聯的屬性：

   - 在 [命令列] 中指定命令，就像是在命令提示字元中指定一樣。 指定有效的命令或批次檔，以及任何必要的輸入或輸出檔。 在批次檔的名稱前面指定**呼叫**批次命令，以保證所有後續命令都會執行。

      您可以使用 MSBuild 巨集透過符號指定多個輸入和輸出檔。 如需如何指定檔案位置或檔案集名稱的資訊，請參閱[建置命令和屬性的一般巨集](../ide/common-macros-for-build-commands-and-properties.md)。

      由於 MSBuild 會保留 '%' 字元，因此如果您指定環境變數，請以 **%25** 十六進位逸出序列取代每個 **%** 逸出字元。 例如，以 **%25WINDIR%25** 取代 **%WINDIR%**。 MSBuild 會在存取環境變數之前，以 **%** 字元取代每個 **%25** 序列。

   - 在 [描述] 中，鍵入此事件的描述。 當此事件發生時，會將描述列印至 [輸出] 視窗。

   - 如果您不想要執行事件，請在 [從組建排除] 中指定 [是]。

## <a name="see-also"></a>另請參閱

[了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)  
[建置命令和屬性的一般巨集](../ide/common-macros-for-build-commands-and-properties.md)  
[為組建自訂進行疑難排解](../ide/troubleshooting-build-customizations.md)  
