---
title: 將字串從一個資源檔移到另一個 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], moving between files
- resource script files, moving strings
- string editing, moving strings between resources
- String editor, moving strings between files
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1bb0c91473e0e3a565bf2a1a7273a35eb3ea5916
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607022"
---
# <a name="moving-a-string-from-one-resource-file-to-another"></a>將字串從一個資源檔移至另一個資源檔

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>若要將字串移到另一個資源指令碼檔案

1. 在這兩個.rc 檔案開啟字串資料表。 (如需詳細資訊，請參閱 <<c0> [ 檢視資源在資源指令碼檔案外部的專案](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。)

   > [!NOTE]
   > 如果您的專案尚未包含 .rc 檔，請參閱 [建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。

2. 以滑鼠右鍵按一下您想要移動，然後選擇 的字串**剪下**從捷徑功能表。

3. 將游標放在目標**字串值編輯器**視窗。

4. 在.rc 檔案中您要移動的字串，以滑鼠右鍵按一下，然後選擇 **貼上**從捷徑功能表。

   > [!NOTE]
   > 如果**識別碼**或**值**移動的字串衝突與現有的**識別碼**或是**值**在目的地檔案中，任一**識別碼**或**值**移動的字串的變更。 如果字串已存在具有相同**識別碼**，則**識別碼**移動的字串的變更。 如果字串已存在具有相同**值**，則**值**移動的字串的變更。

如需將資源加入 managed 專案 （其為目標的通用語言執行平台） 的資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[逐步解說： 當地語系化 Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5)並[逐步解說： 使用資源以利用 ASP.NET 進行當地語系化](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。

## <a name="requirements"></a>需求

Win32

## <a name="see-also"></a>另請參閱

[字串編輯器](../windows/string-editor.md)  
[資源檔](../windows/resource-files-visual-studio.md)  
[自訂視窗版面配置](/visualstudio/ide/customizing-window-layouts-in-visual-studio)  