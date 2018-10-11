---
title: 將字串從一個資源檔移到另一個 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0d8ebfc8f1111049368a76a9b153fcf8079a4edd
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49081854"
---
# <a name="moving-a-string-from-one-resource-file-to-another-c"></a>將字串從一個資源檔移到另一個 （c + +）

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>若要將字串移到另一個資源指令碼檔案

1. 在這兩個.rc 檔案開啟字串資料表。 (如需詳細資訊，請參閱 <<c0> [ 檢視資源在資源指令碼檔案外部的專案](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。)

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 以滑鼠右鍵按一下您想要移動，然後選擇 的字串**剪下**從捷徑功能表。

3. 將游標放在目標**字串值編輯器**視窗。

4. 在.rc 檔案中您要移動的字串，以滑鼠右鍵按一下，然後選擇 **貼上**從捷徑功能表。

   > [!NOTE]
   > 如果**識別碼**或**值**移動的字串衝突與現有的**識別碼**或是**值**在目的地檔案中，任一**識別碼**或**值**移動的字串的變更。 如果字串已存在具有相同**識別碼**，則**識別碼**移動的字串的變更。 如果字串已存在具有相同**值**，則**值**移動的字串的變更。

如需將資源加入 managed 專案 （其為目標的通用語言執行平台） 的資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[逐步解說： 當地語系化 Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[字串編輯器](../windows/string-editor.md)<br/>
[資源檔](../windows/resource-files-visual-studio.md)<br/>
[自訂視窗版面配置](/visualstudio/ide/customizing-window-layouts-in-visual-studio)  