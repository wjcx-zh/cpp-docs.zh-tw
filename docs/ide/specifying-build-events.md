---
title: "指定建置事件 |Microsoft 文件"
ms.custom: 
ms.date: 12/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
dev_langs: C++
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
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 825eec000a2b08bd7a5a4d7769405df2f5570523
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="specifying-build-events"></a>指定建置事件

若要指定連結的程序之前, 在建置開始之前，或組建完成後執行的命令，您可以使用建置事件。

只有在建置成功到達建置流程中的這些點時，建置事件才會執行。 在組建中發生錯誤時*建置後*不會發生事件; 如果發生錯誤之前的連結階段，兩者都不*連結前*和*建置後*事件就會發生。 此外，如果沒有檔案需要連結，*連結前*事件不會發生。 *連結前*事件也不是出現在專案中未包含連結步驟。

如果要建置不需要任何檔案，就會不發生任何建置事件。

一般建置事件的詳細資訊，請參閱[了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)。

### <a name="to-specify-a-build-event"></a>若要指定建置事件

1. 在 [方案總管] 中，選取您想要指定建置事件的專案。

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。

1. 在**建置事件**資料夾中，選取 建置事件屬性頁。

1. 指定建置事件相關聯的屬性：

   - 在**命令列**，如同您已指定它在命令提示字元中指定的命令。 指定有效的命令或批次檔和任何必要輸入或輸出檔案。 指定**呼叫**批次命令批次檔的名稱前面，保證會執行所有後續的命令。

      可以使用 MSBuild 巨集以透過符號指定多個輸入和輸出檔案。 如需如何指定檔的位置或檔案集的名稱資訊，請參閱[建置命令和屬性的一般巨集](../ide/common-macros-for-build-commands-and-properties.md)。

      因為 '%' 字元保留 MSBuild，如果您指定的環境變數取代每個 **%** 逸出字元與**%25**十六進位逸出序列。 例如，取代**%WINDIR%**與**%25WINDIR %25**。 MSBuild 會取代每個**%25**順序與 **%** 字元之前存取環境變數。

   - 在**描述**，輸入此事件的描述。 描述列印至**輸出**視窗時就會發生此事件。

   - 在**從組建排除**，指定**是**如果您不想要執行的事件。

## <a name="see-also"></a>另請參閱

[了解自訂建置步驟和建置事件](../ide/understanding-custom-build-steps-and-build-events.md)  
[建置命令和屬性的一般巨集](../ide/common-macros-for-build-commands-and-properties.md)  
[為組建自訂進行疑難排解](../ide/troubleshooting-build-customizations.md)  
